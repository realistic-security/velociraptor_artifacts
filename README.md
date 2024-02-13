# velociraptor_artifacts

<div style="text-align:center"><img src="./docs/images/stand-logo-400x160.png"/></div>

Welcome to  velociraptor_artifacts repository, This collection is a set of meticulously developed artifacts designed to enhance incident response and digital forensics process by extracting valuable evidence data. Our team recognized the need for specific artifacts that does not exist on[Velociraptor tool](https://github.com/Velocidex/velociraptor) and we developed this collection to fill that gap.

## Features

- **Artifacts:** Each folder in this repository represents a Velociraptor artifact, composed of one or more VQL files tailored for the extraction process.

- **Metadata:** 
	
    - **name:** Name of the artifact example `Windows.Forensics.MRU` 
	- **author:** Author's name we use email address 
	- **description:** Brief description of the artifact and its significance in incident response.


## Changes Log

- [Windows.Forensics.AntiForensics.MFT.Date_Change](./Windows.Forensics.AntiForensics.MFT.Date_Change/): 

    - [Windows.Forensic.AntiForensic.MFT.ChangeDate_With_5Zero](./Windows.Forensics.AntiForensics.MFT.Date_Change/Windows.Forensic.AntiForensic.MFT.ChangeDate_With_5Zero.yaml): Beginner adversaries often neglect nanoseconds when examining dates. This artifact now parses $MFT files, identifying rows where the nanoseconds part contains five consecutive zeros.

    - [Windows.Forensic.AntiForensic.MFT.ChangeDate](./Windows.Forensics.AntiForensics.MFT.Date_Change/Windows.Forensic.AntiForensic.MFT.ChangeDate.yaml): This artifact parses $MFT files and retrieves rows for each relevant MFT record where the user-mode timestamp differs from the kernel-mode timestamp.

    - [Windows.Forensic.AntiForensic.MFT.DateChange_Whitelist](./Windows.Forensics.AntiForensics.MFT.Date_Change/Windows.Forensic.AntiForensic.MFT.DateChange_Whitelist.yaml): Parsing $MFT files, this artifact retrieves rows for each applicable MFT record with a user-mode Created date differing from the kernel mode. It excludes records found in our whitelist database.

    - [Windows.Forensic.AntiForensic.NTFS.Timestomp](./Windows.Forensics.AntiForensics.MFT.Date_Change/Windows.Forensic.AntiForensic.NTFS.Timestomp.yaml): This artifact aids in triage by identifying potential time-stomped files within the NTFS file system.

    Note: Due to its thorough analysis, this artifact requires a considerable amount of time to provide comprehensive results (please allocate resources for more than 1 hour).
 
- [Windows.Forensics.Browser.Clear.Downloads_History](./Windows.Forensics.Browser.Clear.Downloads_History/Windows.Forensics.Browser.Clear.Downloads_History.yaml): This entirely new artifact lists the details of browser downloads that do not exist in the browser history (cleared intentionally)

- [Windows.Forensics.Browser.Typing](./Windows.Forensics.Browser.Typing/Windows.Forensic.Browser.Keyboard_Typing.yaml): New feature Detect keyboard typing in browsers (Chrome, Opera, Edge, Brave, Firefox) with Velociraptor.

    Note: Older browsers may lack the required table, requiring traditional investigation practices. Aimed at reducing false positives using newer tables.

- [Windows.Forensics.BrowserCacheExtraction](./Windows.Forensics.BrowserCacheExtraction/Windows.Forensics.BrowserCacheExtraction.yaml): New Artifact Extracts Chrome/Edge/Brave browsers' cache from Windows cache files using the innovative approach of [Chromecacheview](https://www.nirsoft.net/utils/chromecacheview.zip) tool

- [Windows.Forensics.Clipboard](./Windows.Forensics.Clipboard/Windows.Forensics.Clipborad.yaml): This innovative artifact utilizes ActivitiesCache.db to track clipboard activity since Windows 10 version 1803. Prerequisites include enabling clipboard history and sync across devices. Details provided include StartTime, ExpirationTime, decoded ClipboardPayload, source information in Payload, and ActivityType indicating copy or paste events.

- [Windows.Forensics.Known_Good](./Windows.Forensics.Known_Good/): 
    
    - [Windows.Forensics.Enrichment.ApiHashLookup](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.ApiHashLookup.yaml): Version 0.1 introduces the ability to submit a hash to circl.lu. This artifact, designed to be invoked from within another artifact, facilitates hash lookup enrichment 
    
    Example usage:      
    
    ```SQL
      SELECT * FROM Artifact.Server.Enrichment.ApiHashLookup(Hash_value=$YOURHASH, Hash_type=$HASHTYPE)
    ```
    
    - [Windows.Forensics.Enrichment.Elastic_SearchAPI](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.Elastic_SearchAPI.yaml): Artifact designed for executing search requests to the Elastic API.
    
    - [Windows.Forensics.HybridAnalysis](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.HybridAnalysis.yaml): Enhance your artifact data by submitting a file hash to Hybrid Analysis for a verdict. The default free API restriction is 200 requests per minute or 2000 requests per hour. This server-type artifact is designed to be called from within other artifacts, providing an additional layer of data enrichment. 
    
    Example usage:

    ```SQL
      SELECT * FROM Artifact.Server.Enrichment.HybridAnalysis(Hash=$YOURHASH)
    ```    
    - [Windows.Forensics.Enrichment.Known_Good_Hash](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.Known_Good_Hash.yaml): This artifact leverages the information from previous artifacts to verify a hash parameter using the Elastic API, determining whether a file is identified as known-good or not

    - [Windows.Forensics.Entrichment.Known_Good_Sync_to_Elastic](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.Known_Good_Sync_to_Elastic.yaml): This server event artifact is utilized for synchronization with the Elastic Database and adds new hash entries upon each execution of the Client.Enrichment.Known_Good_Hash artifact

    - [Windows.Forensics.Entrichment.NistDB](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.NistDB.yaml): Artifact Verifies a hash against a local NIST Database and returns a Verdict column with the values true (Known Good) or false (Seems to be malicious). This server artifact is designed to be invoked from within other artifacts. 
    
    Example usage:
 
    ```SQL
      
      SELECT * FROM Artifact.Server.Enrichment.NistDBLookupKnownGood(Hash_value=$YOURHASH, Hash_type=$HASHTYPE, DB_Location=$DBLOCATION)

    ```
    - [Windows.Forensics.Enrichment.Virustotal](./Windows.Forensics.Known_Good/Windows.Forensics.Enrichment.Virustotal.yaml): This Artifact Submit a file hash to VirusTotal for detailed analysis. The default Public API restriction is 4 requests per minute. This server-type artifact is designed to be called from within other artifacts, enhancing the available data. 
    
    Example usage:
 
    ```SQL
      
      SELECT * FROM Artifact.Server.Enrichment.Virustotal(Hash=$YOURHASH)

    ```

- [Windows.Forensics.MozilaCacheExtraction](./Windows.Forensics.MozilaCacheExtraction/Windows.Forensics.MozilaCacheExtraction.yaml): This artifact extracts Mozilla browser cache from Windows cache files. The extraction is performed on the client side. 

- [Windows.Forensics.MRU](./Windows.Forensics.MRU/Winodows.Forensics.MRU.yaml): This artifact is an augmentation for `Windows.Timeline.Registry.RunMRU` where the last does not useless on all case here where we use an This artifact utilizes RECmd from Eric Zimmerman's Tools to analyze User Configuration and Activity, focusing on Most Recently Used (MRU) items. Specifically, it extracts information from the output files LastVisitedPidlMRU__NTUSER.DAT.csv and OpenSavePidlMRU__NTUSER.DAT.csv.

- [Windows.Forensics.RDPCacheBitmapFiles](./Windows.Forensics.RDPCacheBitmapFiles/): 

    - [Windows.Forensics.RDPCachBitmapFiles](./Windows.Forensics.RDPCacheBitmapFiles/Windows.Forensics.RDPCacheBitmapFiles.yaml): This is a custom artifact Where is continue the incident response procedure that `Windows.Forensics.RDPCache` where this one do the same thing and extract bitmap images files from RDP cache file then upload them specifcly for each user in zip file. as shown in the poc 
    

    
    - [Windows.Forensics.RDPCacheServerSide](./Windows.Forensics.RDPCacheBitmapFiles/Windows.Forensics.RDPCacheServerSide.yaml): This server artifact is intended to execute the Windows.Forensics.RDPCacheBitmapFiles collection on a specific client_id provided as an argument. It then passes the images to a self-hosted web app to collect bitmap images of each user, providing a clear picture of RDP cache images. 
    
    - [Windows.Forensics.RDPCacheServerSide.All](./Windows.Forensics.RDPCacheBitmapFiles/Windows.Forensics.RDPCacheServerSide.All.yaml): This artifact utilizes Windows.Forensics.RDPCacheServerSide on all clients, displaying the hostname along with URLs to RDP cache images for each user on the client.

- [Windows.Forensics.ThumbCacheImageExtraction](./Windows.Forensics.ThumbCacheImageExtraction/): 

    - [Windows.SystemIndex_PropertyStore](./Windows.Forensics.ThumbCacheImageExtraction/Windows.SystemIndex_PropertyStore.yaml): This artifact retrieves the SystemIndex_PropertyStore Table from the Windows.edb, drawing inspiration from the [SQLiteHunter](https://github.com/Velocidex/SQLiteHunter?tab=readme-ov-file) artifacts 

    - [Windows.Forensics.ThumbCacheImageExtraction](./Windows.Forensics.ThumbCacheImageExtraction/Windows.Forensics.ThumbCacheImageExtraction.yaml): This artifact extracts cached images from Windows thumbnail cache files. It utilizes Windows.SystemIndex_PropertyStore to specifically target deleted images by searching for their thumbcacheID in the Windows Search index. If the ID doesn't exist, it will be extracted on the client side. The result produces multiple zip files, each associated with a user on each client.

## Usage

1. Clone this repository to your local machine.
2. Navigate to the desired artifact folder.
3. Review the VQL file(s) for the artifact's specific extraction process then imported to [Velociraptor](https://github.com/Velocidex/velociraptor) 


## License

This project is licensed under the [Apache-2.0 license](https://github.com/realistic-security/velociraptor_artifacts?tab=Apache-2.0-1-ov-file#).

## Acknowledgments

We would like to express our gratitude to the Velociraptor community for their support and inspiration.

