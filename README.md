# BypassAntiVirus

**本文为Tide安全团队成员`重剑无锋`原创文章，转载请声明出处！**

**郑重声明：文中所涉及的技术、思路和工具仅供以安全为目的的学习交流使用，任何人不得将其用于非法用途以及盈利等目的，否则后果自行承担！**

---

一直从事web安全多一些，对waf绕过还稍微有些研究，但是对远控免杀的认知还大约停留在ASPack、UPX加壳、特征码定位及修改免杀的年代。近两年随着hw和红蓝对抗的增多，接触到的提权、内网渗透、域渗透也越来越多。攻击能力有没有提升不知道，但防护水平明显感觉提升了一大截，先不说防护人员的技术水平如果，最起码各种云WAF、防火墙、隔离设备部署的多了，服务器上也经常能见到安装了杀软、软waf、agent等等，特别是某数字杀软在国内服务器上尤为普及。这个时候，不会点免杀技术就非常吃亏了。

但web狗一般对逆向和二进制都不大熟，编译运行别人的代码都比较费劲，这时候就只能靠现成的工具来曲线救国了。为此，我从互联网上搜集了大约20款知名度比较高的免杀工具研究免杀原理及免杀效果测试，后面还学习了一下各种语言编译加载shellcode的各种姿势，又补充了一些白名单加载payload的常见利用，于是就有了这一个远控免杀的系列文章。

- **工具篇内容**：msf自免杀、Veil、Venom、Shellter、BackDoor-Factory、Avet、TheFatRat、Avoidz、Green-Hat-Suite、zirikatu、AVIator、DKMC、Unicorn、Python-Rootkit、ASWCrypter、nps_payload、GreatSCT、HERCULES、SpookFlare、SharpShooter、CACTUSTORCH、Winpayload等。

- **代码篇内容**：C/C++、C#、python、powershell、ruby、go等。

- **白名单内容**：总计涉及113个白名单程序，包括Rundll32.exe、Msiexec.exe、MSBuild.exe、InstallUtil.exe、Mshta.exe、Regsvr32.exe、Cmstp.exe、CScript.exe、WScript.exe、Forfiles.exe、te.exe、Odbcconf.exe、InfDefaultInstall.exe、Diskshadow.exe、PsExec.exe、Msdeploy.exe、Winword.exe、Regasm.exe、Regsvcs.exe、Ftp.exe、pubprn.vbs、winrm.vbs、slmgr.vbs、Xwizard.exe、Compiler.exe、IEExec.exe、MavInject32、Presentationhost.exe、Wmic.exe、Pcalua.exe、Url.dll、zipfldr.dll、Syncappvpublishingserver.vbs等。

- **其他内容**：在整个免杀系列文章编写过程中，还穿插写了几篇免杀实践的文章，比如shellcode免杀实践、cs免杀实践、mimikatz免杀实践等几篇文章，水平比较一般，各位小伙伴凑合着看吧。
