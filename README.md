# velociraptor_artifacts

![Realistic Security](./docs/images/stand-logo-400x160.png)


Welcome to  velociraptor_artifacts repository! We made these tools to help with incidents. This collection is a set of carefully developed artifacts designed to improve digital forensics and incident response procedures by extracting important evidence data. Our team recognized the need for specific artifacts that does not exist on [Velociraptor tool](https://github.com/Velocidex/velociraptor) and we developed this collection,  It's our way of trying to fill a gap and make things a bit easier for everyone.

## Features

- **Artifacts:** Each folder in this repository represents a Velociraptor artifact, composed of one or more VQL files tailored for the extraction process.

- **Metadata:** 
	
  - **name:** Name of the artifact example `Windows.Forensics.MRU` 
  - **author:** Author's name we use email address 
  - **description:** Brief description of the artifact and its significance in incident response.


## Changes Log

- [Windows.Forensics.Browser.Clear.Downloads_History](./Windows.Forensics.Browser.Clear.Downloads_History/) 

- [Windows.Forensics.Browser.Typing](./Windows.Forensics.Browser.Typing/)

- [Windows.Forensics.BrowserCacheExtraction](./Windows.Forensics.BrowserCacheExtraction/)

- [Windows.Forensics.Clipboard](./Windows.Forensics.Clipboard/)

- [Windows.Forensics.MozilaCacheExtraction](./Windows.Forensics.MozilaCacheExtraction/):  

- [Windows.Forensics.MRU](./Windows.Forensics.MRU/)

- [Windows.Forensics.RDPCacheBitmapFiles](./Windows.Forensics.RDPCacheBitmapFiles/)

- [Windows.Forensics.ThumbCacheImageExtraction](./Windows.Forensics.ThumbCacheImageExtraction/)


## Usage

1. Clone this repository to your local machine.
2. Navigate to the desired artifact folder.
3. Review the VQL file(s) for the artifact's specific extraction process then imported to [Velociraptor](https://github.com/Velocidex/velociraptor) 


## License

This project is licensed under the [Apache-2.0 license](https://github.com/realistic-security/velociraptor_artifacts?tab=Apache-2.0-1-ov-file#).

## Acknowledgments

We would like to express our gratitude to the Velociraptor community for their support and inspiration.

