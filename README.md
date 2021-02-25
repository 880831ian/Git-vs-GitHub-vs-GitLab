# Git-vs-GitHub-vs-GitLab
# Git vs GitHub vs GitLab

**資料來源（以下為筆記備份，版權歸以下作者所有）**
>Git：https://backlog.com/git-tutorial/tw/intro/intro1_2.html

>Git vs GitHnb：https://tw.alphacamp.co/blog/git-github-version-control-guide

>Git術語對照表：https://www.itread01.com/content/1543581242.html 

# Git 是什麼？

**Git為<font color='red'>分散式版本控制系統</font>，是為了更好管理Linux內核而開發的。<br>
Git可以把檔案的狀態作為更新歷史記錄保存起來。因此可以把編輯過的檔案復原到以前的狀態，也可以顯示編輯過內容的差異。**

**會追蹤每次的Commit的**

* 更動前 vs 更動後的程式碼
*  修改者
*  修改時間
*  修改原因（修改者可自行加入Commit Message）

**且Git單位變動是已<font color='red'>行</font>為計算，追蹤同一個檔案裡每一行程式碼的更動紀錄**

**<font color='blue'>下方介紹Git各項術語</font>**

* 複製（Clone）複製遠端儲存庫，可以將遠端儲存庫上的內容全部下載
* 拉取（Pull）將遠端儲存庫的修改歷史同步到本地儲存庫
* 推送（Push）將本地儲存庫的修改歷史共享至遠端儲存庫上．此外遠端儲存庫的修改歷史，也會與本地儲存庫修改歷史同步
* 獲取（Fetch）確認遠端儲存庫的內容，而不會合併。
* 提交（Commit）將檔案加入索引中，Commit Message 只提交的說明文字
* 分支（Branch）為了將修改記錄的整體流程分開儲存，讓分開的分支不會受到其他分支的影響，分支會分成兩種，一種是Integration分支跟Topic分支，因為其他分支都是建立在Integration上，所以要保持Integration的穩定性，通常master會被當作Integration分支使用，然而master代表本地儲存庫，orgin/master代表遠端儲存庫
    1. 檢出（Checkout）進行分支的切換，執行後，工作目錄裡的檔案會根據切換到不同的分支，而呈現切換後分支的最後提交的內容
    2. 頭指標（Head）指當前分支的最新提交名稱
    3. 儲藏（stash）未提交的修改內容，留在工作目錄下尚未提交情況下Checkout會失敗，這時要先提交修改內容或是將修改內容放入stash中暫時儲存在進行Checkout
    4.  合併（Mergr）完成的Topic分支，最終都會合併到Integration分支
    5.  改寫提交（Revert）如遇到新版程式錯誤，也可以快速切回舊版本，取消添加Pull


# GitHub

**是一個集成Git的服務，也是開源軟體的平台，適合拿來放些作品集、共同編輯的文案等，只要有人對文案進行改動，GitHub也會記錄下改動時間、編輯者等相關資訊，也可以在更動檢查後再與原版合併**

* 優點 ： 是一個可以放開源程式碼的平台，讓需要的人可以自行尋找程式碼並下載使用。
*  缺點 ： 程式碼都是開放的，雖然免費版就有Private可以來限制瀏覽，但提供數量只有3個，對於公司來說往往不夠。（於2019年初，GitHub宣布，免費版開放不限量的創建Private儲存庫）

# GitLab 架設

可以查看 [GitLab 架設](https://github.com/880831ian/GitLab)。

# GitLab GUI 新增SSH

![image](https://raw.githubusercontent.com/880831ian/Git-vs-GitHub-vs-GitLab/main/images/1.png)

**以下範例**

**進入到Git GUI後選擇所安裝的版本(GitLab CE)，以及主機(10.211.55.9)，帳號名稱**

  * 接下來步驟
      1. 先至GitLab網頁上找到Access Tokens
      2. 填寫名稱、到期日、範圍，會產生一組token
      3. 把token帶入到Password內
      4. Protocol選擇SSH，若選擇HTTPS，則不需要SSH Key
      5. SSH Key選擇Generate Key，Passphrase 可直接省略，GUI會自行帶入（.pub）公鑰，檔案會在/.~ssh/下，私鑰要保護好不要被有心人士竊取。
      6. 開啟Terminal，輸入 ``` pbcopy < ~/.ssh/第5點產生的.pub ```
      7. 到GitLab網頁上找到SSH Key
      8. 把第六點複製的貼上Key，設定名稱、到期日，會產生一組token

![image](https://raw.githubusercontent.com/880831ian/Git-vs-GitHub-vs-GitLab/main/images/2.png)

![image](https://raw.githubusercontent.com/880831ian/Git-vs-GitHub-vs-GitLab/main/images/3.png)



#三個比較 Git vs GitHub vs GitLab

| 比較 |  Git  | GitHub | GitLab | 
| :-: |  :-:  | :-: | :-: |
| 優點 |  1. 版本控制工具<br>2. 適合分布式開發（branch）<br>3. 速度快且靈活<br>4. 可離線工作  | 1. 開源軟體平台<br>2. 可以看到其他人開源程式碼 | 1. 可自行架設於公司或私人<br>2. 方便團隊進行issue指派<br>3. CI/CD持續整合、交付、部署 | 
| 缺點 |  1. 學習週期相對長<br>2. 不符合常規思維<br>3. 保密性差 | 1. 程式碼都是開源，保密性差 |  |




```sh
sudo vim /etc/gitlab/gitlab.rb
```

**找到external_url，修改為自己的url及Port (如有修改需要重新GitLab的環境)**

<br>



**跑完腳本如都顯示安裝成功，代表完成**

<br>

