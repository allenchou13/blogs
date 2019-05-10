# C#注册表操作

## 获取顶级注册表项

- 计算机\HKEY_LOCAL_MACHINE: `Registry.LocalMachine`
- 计算机\HKEY_CURRENT_USER: `Registry.CurrentUser`

## 获取注册表项

假设注册表项路径为：`HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\PFU`

代码:

```cs
    var key = Registry.CurrentUser.OpenSubKey(@"HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\PFU");
    if(key == null)
    {
        // not exists
    }
```

## 获取值

```cs
    var key = Registry.CurrentUser.OpenSubKey(@"SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths\AAA");
    var defaultValue = key.GetValue("");
    var pathValue = key.GetValue("Path");
```

## 设置值

```cs
    var key = Registry.CurrentUser.OpenSubKey(@"SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths\AAA");
    key.SetValue("", "default value");
    key.GetValue("Path", "path value");
```