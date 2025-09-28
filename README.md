# 2015-MacBook-Air-Instll-MiniOS

[![](https://github.com/TechTutoPPT/2015-MacBook-Air-Instll-MiniOS/blob/main/cover.PNG)](https://youtu.be/QqSFw5GN8xM)

承接上一影片, MiniOS一樣很重要的功用就是救機, 但今次救機的方式有點不一樣, 因為我手上這部MackBook Air完全沒有硬件上的損壞, 
亦能正常開機進入OS, 只是因年代久遠很多軟件已不再支援這代OS X Yosemite, 連內置的Safair都因證書過期無法瀏覽網站, 難道這部
MacBook Air就只能淪落為打字機嗎? 當然不是, 我就好好應用上一影片講過的MiniOS快速部署的方法, 我的打算是將MacBook Air的硬碟
分割一半容量給MiniOS使用, 保留OS X作為留諗^^.

由於MiniOS本身沒有內置對MacBook Air的WiFi驅動, 所以先用MiniOS隨身碟啟動其他能上網的電腦並安裝以下驅動套件:
```
sudo apt update
sudo apt install dkms broadcom-sta-dkms firmware-b43-installer
```

然後開啟MacBook Air以內置的磁碟工具程式為硬碟壓縮釋出一半空間, 再將其格式化為FAT32, 做法是:
點選Macintosh HD>點選分割>調整以釋出的空間並套用>點選這未分配的空間>點+按鈕>輸入分區名稱>格式選MS-DOS (FAT)>調整分區大小再按套便完成.

最後只要將USB隨身碟中MiniOS相關的所有檔案抄寫到這個FAT32分區內便完成將MiniOS安裝到硬碟了, 重新開機時聽到一下響聲後馬上按下option鍵
便會出現EFI啟動選項, 選Macintosh HD是進入OS X, 選EFI Boot就是進入MiniOS了.

假如開機時你沒有按option鍵, 那預設是啟動OS X的, 若要改為預設啟動MiniOS可於OS X終端機內執行以下步驟:
先執行df -h查看MiniOS分區是否已掛載, 確認後再執行: 
```
sudo bless --mount /Volumes/MINIOS --setBoot
```
這樣預設的啟動系統便會改為MiniOS.

