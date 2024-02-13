# velociraptor_artifacts

Welcome to  velociraptor_artifacts repository, This collection is a set of meticulously developed artifacts designed to enhance incident response and digital forensics process by extracting valuable evidence data. Our team recognized the need for specific artifacts that does not exist on[Velociraptor tool](https://github.com/Velocidex/velociraptor) and we developed this collection to fill that gap.

## Features

- **Artifacts:** Each folder in this repository represents a Velociraptor artifact, composed of one or more VQL files tailored for the extraction process.

- **Metadata:** 
	
    - **name:** Name of the artifact example `Windows.Forensics.MRU` 
	- **author:** Author's name we use email address 
	- **description:** Brief description of the artifact and its significance in incident response.

## Usage

1. Clone this repository to your local machine.
2. Navigate to the desired artifact folder.
3. Review the VQL file(s) for the artifact's specific extraction process then imported to [Velociraptor](https://github.com/Velocidex/velociraptor) 

## Changes Log

- [Windows.Forensics.AntiForensics.MFT.Date_Change](./Windows.Forensics.AntiForensics.MFT.Date_Change/): 
    - Windows.Forensic.AntiForensic.MFT.ChangeDate_With_5Zero: Beginner adversaries often neglect nanoseconds when examining dates. This artifact now parses $MFT files, identifying rows where the nanoseconds part contains five consecutive zeros.

    - Windows.Forensic.AntiForensic.MFT.ChangeDate: This artifact parses $MFT files and retrieves rows for each relevant MFT record where the user-mode timestamp differs from the kernel-mode timestamp.

    - Windows.Forensic.AntiForensic.MFT.DateChange_Whitelist: Parsing $MFT files, this artifact retrieves rows for each applicable MFT record with a user-mode Created date differing from the kernel mode. It excludes records found in our whitelist database.

    - Windows.Forensic.AntiForensic.NTFS.Timestomp: This artifact aids in triage by identifying potential time-stomped files within the NTFS file system.

    Note: Due to its thorough analysis, this artifact requires a considerable amount of time to provide comprehensive results (please allocate resources for more than 1 hour).
 
- [Windows.Forensics.Browser.Clear.Downloads_History](./Windows.Forensics.Browser.Clear.Downloads_History/): This entirely new artifact lists the details of browser downloads that do not exist in the browser history (cleared intentionally)

- [Windows.Forensics.Browser.Typing](./Windows.Forensics.Browser.Typing/): New feature Detect keyboard typing in browsers (Chrome, Opera, Edge, Brave, Firefox) with Velociraptor.

    Note: Older browsers may lack the required table, requiring traditional investigation practices. Aimed at reducing false positives using newer tables.

- [Windows.Forensics.BrowserCacheExtraction](./Windows.Forensics.BrowserCacheExtraction/): New Artifact Extracts Chrome/Edge/Brave browsers' cache from Windows cache files using the innovative approach of [Chromecacheview](https://www.nirsoft.net/utils/chromecacheview.zip) tool

- [Windows.Forensics.Clipboard](./Windows.Forensics.Clipboard/): This innovative artifact utilizes ActivitiesCache.db to track clipboard activity since Windows 10 version 1803. Prerequisites include enabling clipboard history and sync across devices. Details provided include StartTime, ExpirationTime, decoded ClipboardPayload, source information in Payload, and ActivityType indicating copy or paste events.

- [Windows.Forensics.Known_Good](./Windows.Forensics.Known_Good/): 
    - Windows.Forensics.Enrichment.ApiHashLookup: Version 0.1 introduces the ability to submit a hash to circl.lu. This artifact, designed to be invoked from within another artifact, facilitates hash lookup enrichment For example: 
