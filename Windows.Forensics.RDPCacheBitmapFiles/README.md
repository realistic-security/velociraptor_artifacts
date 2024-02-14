# Windows.Forensics.RDPCacheBitmapFiles


- [Windows.Forensics.RDPCachBitmapFiles](./Windows.Forensics.RDPCacheBitmapFiles.yaml): This is a custom artifact Where is continue the incident response procedure that `Windows.Forensics.RDPCache` where this one do the same thing and extract bitmap images files from RDP cache file then upload them specifcly for each user in zip file. as shown in the poc 
    

- [Windows.Forensics.RDPCacheServerSide](./Windows.Forensics.RDPCacheServerSide.yaml): This server artifact is intended to execute the Windows.Forensics.RDPCacheBitmapFiles collection on a specific client_id provided as an argument. It then passes the images to a self-hosted web app to collect bitmap images of each user, providing a clear picture of RDP cache images. 
    
- [Windows.Forensics.RDPCacheServerSide.All](./Windows.Forensics.RDPCacheServerSide.All.yaml): This artifact utilizes Windows.Forensics.RDPCacheServerSide on all clients, displaying the hostname along with URLs to RDP cache images for each user on the client.

