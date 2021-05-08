# Doisnet
Solve any network problem

<img alt="GitHub release (by tag)" src="https://img.shields.io/github/downloads/dodois/Doisnet/v0.0.1/total?style=flat-square">&nbsp;<img alt="GitHub" src="https://img.shields.io/github/license/dodois/Doisnet?style=flat-square">&nbsp;<img alt="GitHub stars" src="https://img.shields.io/github/stars/dodois/Doisnet?style=flat-square">

[Windows版下载](https://hub.fastgit.org/dodois/Doisnet/releases/download/v0.0.1/doisnet-0.0.1.Setup.exe)

## 病毒威胁防范
大部分安全软件默认将 ```powershell``` 脚本标识为病毒，后缀名为 ```.ps1```

为缩小应用体积 ```Doisnet``` 采用 ```wininet-reset-settings.ps1``` 脚本设置系统代理

### wininet-reset-settings.ps1
```
$signature = @'
[DllImport("wininet.dll", SetLastError = true, CharSet=CharSet.Auto)]
public static extern bool InternetSetOption(IntPtr hInternet, int
dwOption, IntPtr lpBuffer, int dwBufferLength);
'@

$interopHelper = Add-Type -MemberDefinition $signature -Name MyInteropHelper -PassThru
$INTERNET_OPTION_SETTINGS_CHANGED = 39
$INTERNET_OPTION_REFRESH = 37

$result1 = $interopHelper::InternetSetOption(0, $INTERNET_OPTION_SETTINGS_CHANGED, 0, 0)
$result2 = $interopHelper::InternetSetOption(0, $INTERNET_OPTION_REFRESH, 0, 0)

$result1 -and $result2
```


