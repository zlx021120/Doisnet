# Doisnet
<h6>Solve any network problem</h6>
<img align="right" src="https://user-images.githubusercontent.com/73285310/117543679-68f9b680-b050-11eb-9286-7d806d6f5f08.png">
<p>
<img alt="GitHub release (by tag)" src="https://img.shields.io/github/downloads/dodois/Doisnet/v0.0.1/total?style=flat-square">&nbsp;<img alt="GitHub" src="https://img.shields.io/github/license/dodois/Doisnet?style=flat-square">&nbsp;<img alt="GitHub stars" src="https://img.shields.io/github/stars/dodois/Doisnet?style=flat-square">
</p>

[:computer:Windows版下载](https://hub.fastgit.org/dodois/Doisnet/releases/download/v0.0.1/doisnet-0.0.1.Setup.exe)

[:apple:Mac版下载](https://github.com/dodois/Doisnet/issues/3)

## 病毒威胁防范
大部分安全软件默认将 ```powershell``` 脚本标识为病毒，后缀名为 ```.ps1```

为缩小应用体积 [Doisnet](https://github.com/dodois/Doisnet) 采用 ```wininet-reset-settings.ps1``` 脚本设置系统代理

### wininet-reset-settings.ps1
```powershell
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

## Apple Developer 证书签名支援
我们缺少可用的苹果开发者ID

该问题导致Mac版 [Doisnet](https://github.com/dodois/Doisnet) 无法正常签名打包.
希望社区的小伙伴能够支援我们有效的开发者ID或证书.
助力Mac版 [Doisnet](https://github.com/dodois/Doisnet) 早日上线.

支援方式：
1. 加入 [TG群组](https://t.me/dosvpn)
2. 邮件 <doisnet@protonmail.com>
