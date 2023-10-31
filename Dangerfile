# commit size
if danger.git.commits.size > 10
  warn("提交数应小于10")
end

# commit title
commit_title = ["update:", "del:", "feat:", "mod:", "refoctor:", "style:", "debug", "[Update]:", "Update"]
if !danger.git.commits.first.message.match(/#{commit_title.join("|")}/)
  warn("提交信息错误 需包含: #{commit_title.join(" 或 ")}")
end

def check()
  diff = `git diff --cached --numstat --summary`
  diff2 = `git diff --numstat --summary`

  diff.gsub!(/(mode )[0-9]{1,}/, "")
  total = 0
  diff.to_s.scan(/\d{1,3}/).each do |num|
    total += num.to_i
  end
  total
end

if check > 100
  warn("请遵循最小commit原则")
end
