
*2 min 一次循环，看当前文本是否改动，循环脚本，占用窗口*

nano ~/autosync.sh



#!/data/data/com.termux/files/usr/bin/bash

REPO=~/storage/shared/obsidian-notes
cd "$REPO" || exit 1

echo "📥 startup pull..."
git pull --rebase --autostash

while true
do
  sleep 120

  if [[ -n $(git status --porcelain) ]] ; then
    echo "🔄 detected changes..."

    git add -A
    git commit -m "auto sync $(date '+%F %T')"
    git push
   else
    echo "✅ idle"
  fi
done


---

*pull+push一次，手动执行，一次性脚本*

nano ~/once.sh



#!/data/data/com.termux/files/usr/bin/bash

REPO=~/storage/shared/obsidian-notes
cd "$REPO" || exit 1

echo "📥 pull..."
git pull --rebase --autostash

echo "🔄 checking..."

# 有改动 → commit + push
if [[ -n $(git status --porcelain) ]] ; then
  git add -A
  git commit -m "auto sync $(date '+%F %T')"
  git push

# 已 commit 但没 push → 直接 push
elif [[ -n $(git log origin/main..HEAD) ]] ; then
  echo "🚀 pushing pending commits..."
  git push

else
  echo "✅ up to date"
fi

---
检测



...ermux/files/home/.shortcuts/status-autosync.sh
#!/data/data/com.termux/files/usr/bin/bash

if pgrep -f autosync.sh > /dev/null
then
  echo "🟢 autosync 正在运行"
else
  echo "🔴 autosync 未运行"
fi

