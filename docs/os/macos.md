# macOS

## 15 已损坏无法打开 允许AnyWhere任何来源的软甲
> XXX is damaged and can’t be opened. You should move it to the Trash
打开运行（Terminal）运行命令：

```
$ sudo spctl --master-disable。
$ sudo xattr -d com.apple.quarantine /Applications/XXX.app
```

## 解压 dmg 
7z x xxx.dmg
7z x xxx.hfs