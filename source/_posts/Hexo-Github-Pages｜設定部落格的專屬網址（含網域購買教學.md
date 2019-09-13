---
title: Hexo + Github Pages：教你設定部落格的專屬網址，含網域購買教學
tags:
  - hexo
  - github
  - github pages
  - 網域購買
  - custom domain
  - blog
categories:
  - - 科技生活
  - - 架站服務
keywords: 'blog, hexo, 部落格, 網域購買, google domain, github pages, github'
abbrlink: 50343
date: 2019-03-19 22:40:35
---

前一篇教大家如何在Github Pages上使用Hexo建立自己的個人部落格，現在要來教大家如何綁定自己的專屬網址啦！

## 如何擁有個人網域？
### 選擇網域註冊商
目前在販賣網域的網站有很多，比較多人在用的有[GoDaddy](https://tw.godaddy.com/)，通常在網路上找個折扣碼的話第一年網址可以用NT$39左右的價格入手.com結尾的網址。但GoDaddy的缺點是如果要加購**隱私權保護服務**[^1]的話，費用會增加為NT$340/年。而第二年網域再續約的時候會回歸原價，加起來會變成NT$655/年。

所以我個人是選擇到[Google Domains](https://domains.google.com/)購買網域，跟Google買的話他會直接送你**隱私權保護服務**的功能，總費用的話是$12/年（約莫NT$370/年），如果打算長期使用的話會比GoDaddy來的划算。

<!--more-->

### Google Domain 購買教學
由於Google Domain目前不支援台灣，故在購買的時候需切換到美國地區。

首先是要搜尋你想要的網域有沒有被別人註冊走，這邊範例搜尋`larrycool.com`尚未有人購買，便可以點擊右方購物車按鈕將其加入購物車。
![搜尋自己要的網域](https://res.cloudinary.com/larrynote/image/upload/v1567305909/larrynotepost/images9_ve2tkj.png)

建議將**隱私權保護服務**啟用，關閉自動續約。
![啟用隱私權保護服務](https://res.cloudinary.com/larrynote/image/upload/v1567305909/larrynotepost/images10_iyfkgx.png)

這邊可以填自己的真實的聯絡地址即可。
![連絡資訊](https://res.cloudinary.com/larrynote/image/upload/v1567305909/larrynotepost/images11_rty1tw.png)

這個地方的地區就要選美國了，隨便到網路上找個郵遞區號填入即可。我在這邊是填入「91101」這個郵遞區號，是美國加州的帕薩迪納城市。
![帳單資訊](https://res.cloudinary.com/larrynote/image/upload/v1567305909/larrynotepost/images12_p8yflm.png)

現在你成功地擁有自己的網址啦！

## 簡單四步驟，輕鬆設定個人網域
剛剛購買了屬於自己的網址，現在要來教大家如何把這串網址跟你的部落格做綁定。

### 步驟1：讓Github Page知道你的自訂網域
1. 到Github專案的setting中
2. 在Custom domain中新增自己的自訂網域，建議以www做開頭
![Github專案中新增Custom domain](https://res.cloudinary.com/larrynote/image/upload/v1567305909/larrynotepost/images13_kndzq4.png)

### 步驟2：將自訂網域導向Github Pages
1. 到Google Domain中選擇你剛剛購買的網址
2. 到DNS中的Custom resource records
3. 因為網站是架在Github上面，所以我們要增加4條A紀錄（ [Github官方提供列表](https://help.github.com/articles/setting-up-an-apex-domain/#configuring-a-records-with-your-dns-provider) ），將所有指向「自訂網域」的流量導向Github的伺服器
	* 185.199.111.153
	* 185.199.110.153
	* 185.199.109.153
	* 185.199.108.153
4. 增加CNAME紀錄為你的網域新增別名，讓輸入`reponame.github.io.`網址的人也能導向你剛剛購買的網域

前方填入www，後方填入Github Pages的專案名稱
![Google Domain設定A record和CNAME](https://res.cloudinary.com/larrynote/image/upload/v1567305909/larrynotepost/images14_brw11j.png)

#### 步驟3：強力推薦開啟https選項
到專案的setting中的custom domain中點選Enforce HTTPS

#### 步驟4：到hexo的source資料夾內新增`CANME`檔案，裡面寫上你剛剛購買的域名，避免在執行`hexo generate`產生新動態檔案的時候會覆蓋Github Pages setting內的域名。

檔案內的設定如下(xxx替換成你剛剛購買的網域名稱)
```
www.xxx.com
```

## 修改Hexo的網站配置文件
最後一步就是要來修改Hexo的網站配置文件了，打開`config.yml`檔案，找到url那行，更改程式碼如下：
```
url: http://www.xxx.com/
root: /
```

接下來試著將網誌用`hexo deploy`上傳到Github上面，再輸入你剛剛購買的網域`www.xxx.com`，就可以成功看到你的網誌啦！

就算之後別人輸入`https://username.github.io/reop.github.io`也會自動導向`www.xxx.com`囉！

## 總結
以上是Hexo + Github Pages的服務如何使用自訂網域的教學，如果有任何需要協助的地方都歡迎在下方留言，我會盡我所能幫助你。

如果你還沒使用Hexo架個人網站的話，推薦可以閱讀我寫的[《Hexo + Github Pages｜手把手教你打造免費個人部落格》](https://www.larrynote.com/website-service/6590/)這篇教學文唷！

## 參考資料
* [How to setup google domain for github pages - DEV Community ](https://dev.to/trentyang/how-to-setup-google-domain-for-github-pages-1p58)
* [Setting up an apex domain - GitHub Help](https://help.github.com/en/articles/setting-up-an-apex-domain#configuring-a-records-with-your-dns-provider)

## 備註
[^1]: 如果沒有啟用隱私權保護服務的功能的話，你註冊網域時所填的資料都可以在WHOIS上面被公開查詢，選用有提供這項服務的網域註冊商還是比較安全的。