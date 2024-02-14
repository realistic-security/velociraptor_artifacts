# Windows.Forensics.ThumbCacheImageExtraction

- [Windows.SystemIndex_PropertyStore](./Windows.SystemIndex_PropertyStore.yaml): This artifact retrieves the SystemIndex_PropertyStore Table from the Windows.edb, drawing inspiration from the [SQLiteHunter](https://github.com/Velocidex/SQLiteHunter?tab=readme-ov-file) artifacts 

- [Windows.Forensics.ThumbCacheImageExtraction](./Windows.Forensics.ThumbCacheImageExtraction.yaml): This artifact extracts cached images from Windows thumbnail cache files. It utilizes Windows.SystemIndex_PropertyStore to specifically target deleted images by searching for their thumbcacheID in the Windows Search index. If the ID doesn't exist, it will be extracted on the client side. The result produces multiple zip files, each associated with a user on each client.