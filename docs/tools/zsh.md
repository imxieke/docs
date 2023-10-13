## 默认变量

```bash
%n - username
%m - short name of the current host
%M - name of curent host
%# - a `%` or a `#`, depending on whether the shell is running as root or not
%~ - relative path
%/ or %d - absolute path
%c or %C - Trailing component of the current working directory.
%t - time 12hr am/pm format
%T - time 24hr format
%w - day and date (day-dd)
%D - Date (default: yy-mm-dd)
%D{%f} - day of the month
%l or %y - The line  (tty)  the user is logged in on, without `/dev/' prefix.
```

## ohmyzsh
### 主题定义
```
# 左边的内容
PROMPT=’‘
# 右边的内容
RPROMPT=’’
```

### 颜色定义
```
%F{237} 256 color number
%F{red} 8 color name (black, red, green, yellow, blue, magenta, cyan, white)
$FG[237] (notice the $ sign instead of %) 256 color number
$fg[red] (notice the $ and lower case fg) 8 color name (black, red, green, yellow, blue, magenta, cyan, white)
%{$fg_bold[blue]%} bold variants
%F is Foreground color, $f for resetting foreground color
%K is bacKground color, %k for resetting background-color
$reset_color is a Zsh variable that resets the color of the output
You can use Unicode for symbols
%E Clear to end of the line.
%U (%u) to Start (stop) underline mode.
```