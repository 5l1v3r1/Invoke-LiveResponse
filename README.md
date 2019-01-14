# Invoke-LiveResponse
The current scope of [Invoke-LiveResponse](https://mgreen27.github.io/posts/2018/01/14/Invoke-LiveResponse.html) is a live response tool for targeted collection. There are two main modes of use in Invoke-LiveResponse and both are configured by a variety of command line switches.

### ForensicCopy
* Reflectively loads Powerforensics onto target machine to enable raw disk access.
* Leverages a scriptblock for each configured function of the script. 
* Common forensic artefacts and custom file collections.
* WinPMem for memory support
* Depending on the selected switches, each selected capability is joined at run time to build the scriptblock relevant to usecase.

### Live Response
* Inspired by the Kansa Framework, LiveResponse mode will execute any Powershell scripts placed inside a content folder.
* Results consist of the standard out from the executed content, redirected from the collection machine to a local Results folder as ScriptName.txt.
* The benefit of this method is the ability to operationalise new capability easily by dropping in new content with desired StdOut.

### Installation
1) Download Powershell-IR and rename to Invoke-LiveResponse into Powershell profile.

To run: Import-Module Invoke-LiveResponse

Help: Get-Help Invoke-LiveResponse -detailed


###### One liner install (if you trust me...)
PS> $url="https://raw.githubusercontent.com/mgreen27/Powershell-IR/master/Content/Ancilaries/Get-Forensicating.ps1";[Net.ServicePointManager]::SecurityProtocol = "tls12, tls11, tls";$WebClient=(New-Object System.Net.WebClient);$WebClient.Proxy=[System.Net.WebRequest]::GetSystemWebProxy();$WebClient.Proxy.Credentials=[System.Net.CredentialCache]::DefaultNetworkCredentials;Invoke-Expression $WebClient.DownloadString($url)