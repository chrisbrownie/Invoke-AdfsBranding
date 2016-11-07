# Invoke-AdfsBranding.ps1
After what seemed like hundreds of AD FS deployments involving rebranding exercises, I got sick of following the TechNet article and then weaving my way through the CSS and JavaScript looking for a particular value and the impact it had on the rest of the page. This, Invoke-AdfsBranding.ps1 was born. One quiet weekend later, this has made all my subsequent AD FS deployments a lot easier. Time to focus on making the page pretty, rather than finding that single line of CSS.

This script rebrands the entire environment on each run. As such, I'd advise against making any customisations outside the script, as you may find they don't survive. I'd welcome pull requests to provide further customisation of the AD FS branding.

## Requirements
* Script is tested on Windows Server 2012 R2 and above. As such, it is supported on Windows PowerShell 4.0 and above 
* Script must be run from the primary AD FS server in the farm. Remoting is not yet tested
* It is recommended to follow these AD FS Best Practices guides for [Windows Server 2012 R2](https://flamingkeys.com/ad-fs-3-best-practices/) and [Windows Server 2016](https://flamingkeys.com/ad-fs-windows-server-2016-best-practices/) to ensure your AD FS environment is in good condition, paying particular attention to patch recommendations

## Credits
* Thanks to [Mathias Bynens](https://github.com/mathiasbynens) for [this](https://gist.github.com/mathiasbynens/428626) great gist demonstrating how to change a page's favicon using JavaScript. Since we can't access the root of the domain through the AD FS cmdlets, we use this mechanism to update the AD FS favicon using JavaScript and a `favicon.ico` file in a non-standard path 

## Resources
Microsoft publish two great articles on branding AD FS, but they both assume you're only doing it once, and that you're a CSS/JavaScript ninja. 
* [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/en-us/library/dn280950(v=ws.11).aspx)
* [Advanced Customization of AD FS Sign-in Pages](https://technet.microsoft.com/en-us/library/dn636121(v=ws.11).aspx)