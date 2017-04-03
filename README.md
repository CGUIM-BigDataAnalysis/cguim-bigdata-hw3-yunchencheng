長庚大學 大數據分析方法 作業三
================

install.packages("rvest") \#\# 網站資料爬取

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
PTT <- "https://www.ptt.cc/bbs/LoL/index.html"
PTT02 <- "https://www.ptt.cc/bbs/LoL/index7122.html"
PTT03 <- "https://www.ptt.cc/bbs/LoL/index7121.html"
PTT04 <- "https://www.ptt.cc/bbs/LoL/index7120.html"
PTT05 <- "https://www.ptt.cc/bbs/LoL/index7119.html"
PTT06 <- "https://www.ptt.cc/bbs/LoL/index7118.html"
PTT07 <- "https://www.ptt.cc/bbs/LoL/index7117.html"
PTT08 <- "https://www.ptt.cc/bbs/LoL/index7116.html"
b <- c(PTT,PTT02,PTT03,PTT04,PTT05,PTT06,PTT07,PTT08)
frameAll <- NULL

for(n in b){
    PTTContent <- read_html(n)
    post_title <- PTTContent %>%
        html_nodes(".title") %>%
        html_text()
    post_title
    
    post_nrec <- PTTContent %>%
        html_nodes(".nrec") %>%
        html_text()
    post_nrec
    
    post_author<- PTTContent %>% 
        html_nodes(".author") %>% 
        html_text()
    post_author
    
    post_date<- PTTContent %>% 
            html_nodes(".date") %>% 
            html_text()
    post_date
    
    pppt <- data.frame( title = c(post_title),
                        pushNum = c(post_nrec),
                        author = c(post_author),
                        date = c(post_date) )
    pppt
    
    frameAll <- rbind( frameAll,pppt )
    Sys.sleep(sample(3:5, 1))
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(
    frameAll[1:151,c("title","pushNum","author","date")])
```

| title                                            | pushNum | author       | date  |
|:-------------------------------------------------|:--------|:-------------|:------|
| (本文已被刪除) \[alive211079\]                   | 9       | -            | 4/03  |
| \[實況\] 晴時多雲偶陣雨 火龍果妹                 | 16      | XDos         | 4/03  |
| \[實況\] Troll死你們 草人爬分台                  |         | yulymoon     | 4/03  |
| \[問題\] LCK 飛斯 逆命 雷尼克頓                  | 13      | ezo786       | 4/03  |
| Re: \[閒聊\] 新故事的汎根本是個碧曲吧！？        | 9       | LightEcho    | 4/03  |
| \[問題\] 請問丁特該不該回歸？                    | 4       | s6622156     | 4/03  |
| Re: \[ANSI\] 索娜 Sona                           | 10      | f222051618   | 4/03  |
| Re: \[閒聊\] 新故事的汎根本是個碧曲吧！？        | 10      | Stabberlol   | 4/03  |
| \[揪團\] 快樂的恩居團(滿)                        | 2       | wanchieh     | 4/03  |
| \[公告\] LoL║英雄 ┌──┐４月閒聊區┌→               | 爆      | rainnawind   | 4/02  |
| \[公告\] LoL 英雄聯盟板板規（Patch 17.01.01）    |         | rainnawind   | 1/01  |
| \[電競\] 近期賽事                                | 41      | superRKO     | 11/02 |
| \[實況\] SKT T1 kkOma(關                         | 5       | narutodante  | 4/03  |
| \[問題\] 最快打完前十場的方法                    | 2       | Campione3310 | 4/03  |
| \[情報\] 約德爾人的主題日！兒童節可愛優惠        | 23      | LegendDragon | 4/03  |
| (本文已被刪除) \[ex8338\]                        | 10      | -            | 4/03  |
| \[問題\] 招換師技能互換為何勝率會大增            | 10      | songgood     | 4/03  |
| \[閒聊\] 台服現在最強寇格魔是誰?                 | 78      | seysem       | 4/03  |
| Re: \[閒聊\] Apex回答太狂 還是大魚功力不足？     |         | shintrain    | 4/03  |
| \[問題\] 清明節會有人幫阿姆姆掃墓嗎?             | 39      | iamfenixsc   | 4/03  |
| \[實況\] RPG Evi 韓服 日本隊上路                 | 16      | zxc7         | 4/03  |
| \[閒聊\] 新故事的汎根本是個碧曲吧！？            | 38      | f222051618   | 4/03  |
| Re: \[閒聊\] Apex回答太狂 還是大魚功力不足？     | 5       | joe255118    | 4/03  |
| (已被samhou6刪除) <iloveykk> D1                  | 4       | -            | 4/03  |
| \[ANSI\] 索娜 Sona                               | 55      | shyin7089    | 4/03  |
| \[實況\] 性感荷官 彈性積分五排                   | 3       | MRsoso       | 4/03  |
| (已被samhou6刪除) <starfishkira> D1              | 19      | -            | 4/03  |
| \[實況\] 獸控實況主Dog4ni – 高端魔術秀           | 1       | wuisgod54    | 4/03  |
| \[實況\] I3utterfly0v0/蝴蝶兒&lt;3               |         | airiguodala  | 4/03  |
| \[閒聊\] 為什麼Riot都不出多控英雄                | 25      | azjba89xz    | 4/03  |
| \[實況\]麥麥貝比/今天適合練腳 練到105cm長腿      | 6       | chulashiy    | 4/03  |
| \[閒聊\] 球z跟丁特誰的JG比較強?                  | 22      | womantalk    | 4/03  |
| \[閒聊\] LOL有關於魔道的角色嗎?                  | 8       | iloveykk     | 4/03  |
| (本文已被刪除) \[sky082\]                        |         | -            | 4/03  |
| \[閒聊\] 徵求LMS 4/8門票兩張                     | 5       | iverson242i  | 4/03  |
| \[問題\] 除了opgg有其他網站嗎                    | 3       | disa26118    | 4/03  |
| (本文已被刪除) \[Aatrox5566\]                    | 1       | -            | 4/03  |
| Re: \[閒聊\] Apex回答太狂 還是大魚功力不足？     | 爆      | eltar        | 4/03  |
| \[外絮\] JCRE FB                                 | 爆      | dinter9921   | 4/03  |
| \[閒聊\] LMS 2017 Spring 數據整理(~4/2)          | 40      | fkc          | 4/03  |
| \[影片\] 歐洲最強逆命精華                        | 14      | waiting0212  | 4/03  |
| \[閒聊\] 在傳說啟程發現一件事情                  | 3       | cocoinin     | 4/03  |
| \[實況\] TPS King / GodJJ 回來了                 | 34      | eqer         | 4/03  |
| Re: \[閒聊\] 大家按Q技能會用小拇指嗎?            | 1       | handsomeLin  | 4/03  |
| \[心得\] 國動真的對積分現況有所改革了            | 38      | machiner     | 4/03  |
| \[心得\] 真的很OP－野區暴徒 暴走重砲 吉茵珂絲    |         | x236x55x3    | 4/03  |
| \[閒聊\] 我在召喚峽谷裡得到了救贖                |         | bubuno35     | 4/03  |
| (本文已被刪除) \[ooqr1995tw\]                    |         | -            | 4/03  |
| \[問題\] 會戰找不到自己游標怎麼辦                | 8       | d995511      | 4/03  |
| \[揪團\] 跟女友吵架的單雙（滿                    | 6       | jkonk9527    | 4/03  |
| (本文已被刪除) \[HITTEN\]                        | 1       | -            | 4/03  |
| \[閒聊\] J特真的比動主播好                       | X1      | asd0952      | 4/03  |
| Re: \[問題\] 國動的崛起是否意味著lol走偏了       |         | tigotigo5566 | 4/03  |
| \[問題\] 潘森是線霸嗎?                           | 14      | FrogStar     | 4/03  |
| \[閒聊\] 探討犽宿的風牆效用                      | X2      | Baledu       | 4/03  |
| (本文已被刪除) \[LIN6627\]                       |         | -            | 4/03  |
| \[問題\] 不投降跟風氣差 跟張家兄弟有什麼關係?    |         | godband5566  | 4/03  |
| \[閒聊\] 打野該積極gank嗎                        | X2      | FollowMe6    | 4/03  |
| Re: \[閒聊\] Apex回答太狂 還是大魚功力不足？     |         | birdanderson | 4/03  |
| \[閒聊\] 國棟的鼻地戰術是傳承了中國武術？        | 76      | stu88001     | 4/03  |
| (本文已被刪除) \[qwertytrew\]                    |         | -            | 4/03  |
| \[閒聊\] 賈克斯打sup為啥不行                     |         | tigotigo5566 | 4/03  |
| Re: \[閒聊\] Apex回答太狂 還是大魚功力不足？     | 5       | InnGee       | 4/03  |
| \[問題\] 殞落王者之劍是不是很適合特朗德?         | 33      | FrogStar     | 4/03  |
| \[閒聊\] WS如果要贏到底還缺了甚麼東西?           | 20      | orange0319   | 4/03  |
| \[實況\] 胡瓜太郎 Otofu 台服鑽二Sup遊玩中        | 19      | goodjob622   | 4/03  |
| \[實況\] M17 APEX                                | 爆      | shan0825     | 4/03  |
| \[問題\] ARAM也有高低端場分別嗎?                 | 22      | osbsd1       | 4/03  |
| \[實況\] FW NL / 煞氣o狂by衝崩銨                 | 30      | ns96729      | 4/03  |
| \[閒聊\] 解說記得的正宗中文教學                  | 6       | diefish5566  | 4/03  |
| \[問題\] 丁特有考慮練蒙多醫生JG嗎？              | 2       | ru04ul4      | 4/03  |
| \[閒聊\] HKE韓服成績真的深不可測                 | 8       | stben        | 4/03  |
| \[閒聊\] 會看EU&其他區比賽的人 是用什麼心情在看? | 15      | jakert123    | 4/03  |
| \[外絮\] Peanut安慰沒進入季後賽的Gorilla         | 60      | aaronshell   | 4/03  |
| \[閒聊\] 如果實況界沒統神現在會是甚麼風氣?       | 8       | KENDO777     | 4/03  |
| \[影片\]【國動】被戳到爆氣開啟動粉見面會         | 24      | sky082       | 4/03  |
| Re: \[閒聊\] 如果實況界沒統神現在會是甚麼風氣?   |         | ardan3355    | 4/03  |
| (本文已被刪除) \[asd0952\]                       |         | -            | 4/03  |
| \[揪團\] 金牌彈性-1                              |         | jun12344     | 4/03  |
| \[閒聊\] Apex回答太狂 還是大魚功力不足？         | 51      | Tiandai      | 4/03  |
| \[閒聊\] Weekly LCK Mic check                    | 23      | s80554       | 4/03  |
| (本文已被刪除) \[pttpig\]                        |         | -            | 4/03  |
| Re: \[閒聊\] Apex回答太狂 還是大魚功力不足？     | 51      | bingtsien    | 4/03  |
| (本文已被刪除) \[melon1001\]                     |         | -            | 4/03  |
| \[閒聊\] 有沒有專精克雷德的玩家來交流個          | 43      | silly7995    | 4/03  |
| \[揪團\] 找上白金的夥伴                          | 1       | trollriven   | 4/03  |
| \[揪團\] 銅銀小號雙排                            | 2       | FJUmars      | 4/03  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? | X1      | McHamburger  | 4/03  |
| \[實況\] 刺刺的 韓服 金三                        |         | ym19950822   | 4/03  |
| (本文已被刪除) \[hongou\]                        |         | -            | 4/03  |
| \[實況\] 藍色風暴 龍獸 金牌RANK<sub>~</sub>      |         | pcnetworld   | 4/03  |
| Re: \[問題\] 國動的崛起是否意味著lol走偏了       | 7       | tenshoufly   | 4/03  |
| \[閒聊\] 是不是應該拔除某些玩家的投票權          |         | joshua0606   | 4/03  |
| \[閒聊\] 同人圖分享-你以為有貓我就會推嗎？       | 6       | f222051618   | 4/03  |
| \[閒聊\] 【統神】深夜真性情—那些年的誤會委屈     | 11      | g8320484816  | 4/03  |
| \[閒聊\] 小熊 Yuniko FB                          | 20      | Comebuy      | 4/03  |
| \[ANSI\] 瓦羅然沒有派對                          | 18      | AlzioNever   | 4/03  |
| \[閒聊\] 大家按Q技能會用小拇指嗎?                | 48      | phillp0804   | 4/03  |
| Re: \[問題\] 國動的崛起是否意味著lol走偏了       | 4       | sincossincos | 4/03  |
| Re: \[閒聊\] 這季MVP該給誰                       | 3       | Re12345      | 4/03  |
| \[閒聊\] 一發死的角色是不是逐漸消失中?           | 12      | greattower   | 4/03  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? | 2       | kingion      | 4/03  |
| (本文已被刪除) \[dant123\]                       |         | -            | 4/03  |
| \[發錢\] 國考放榜來猜猜灰鵝喜歡的LCK選手(Done)   | 82      | where1993    | 4/03  |
| \[閒聊\] HKE vs. M17 G2 分析台+國人訪問逐字      | 38      | eltar        | 4/03  |
| Re: \[閒聊\] 大家按Q技能會用小拇指嗎?            | 17      | s930406      | 4/03  |
| Re: \[閒聊\] LMS春季第一隊的上路會是誰？         | 2       | willia5566   | 4/03  |
| Re: \[問題\] 國動的崛起是否意味著lol走偏了       | 11      | arrenwu      | 4/03  |
| Re: \[閒聊\] LMS春季第一隊的上路會是誰？         | 3       | kingion      | 4/03  |
| \[閒聊\] 美板官方粉絲團 FB                       | 17      | Comebuy      | 4/03  |
| \[閒聊\] ROC是不是很悲情？                       | 32      | andy82116    | 4/03  |
| \[電競\] 2017 NA LCS夏季升降賽Day3 NV vs. GCU    | 3       | cherrycheese | 4/03  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? | 爆      | ice91312     | 4/02  |
| \[閒聊\] 是不是只有進入遊戲畫面才知道ping值      | 2       | supereight   | 4/02  |
| \[公告\] 樂透退盤處置說明                        | 78      | rainnawind   | 4/02  |
| Re: \[閒聊\] Gear是不是真的過譽了？              | 29      | Re12345      | 4/02  |
| \[實況\] 獄胤天 清明時節雨紛紛 分分塊來RRR       |         | asdfg5247    | 4/02  |
| \[問題\] 國動的崛起是否意味著lol走偏了           | 10      | fdfdfdfd51   | 4/02  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? | 2       | ArtemXis     | 4/02  |
| \[閒聊\] 這季MVP該給誰                           | 30      | zzsh3533     | 4/02  |
| \[閒聊\] 恭喜M17 (已發)                          | 59      | China666     | 4/02  |
| \[閒聊\] 四強的各路大家覺得強度比較？            | 25      | godshibainu  | 4/02  |
| (已被rainnawind刪除) <frank123ya>                | 31      | -            | 4/02  |
| \[實況\] HKE KuKu / 口口口口口 跟韓國人定輸贏    | 2       | a089069      | 4/02  |
| \[閒聊\] M17要是5人同時醒著 能給前兩隊衝擊嗎?    | 54      | JuicyChen    | 4/02  |
| (本文已被刪除) \[FrogStar\]                      | 15      | -            | 4/02  |
| (本文已被刪除) \[AlzioNever\]                    |         | -            | 4/02  |
| \[外絮\] Kt Score:會拿出如粉絲所期待的表現       | 25      | ubiqui       | 4/02  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? | 3       | wade8204     | 4/02  |
| \[公告\] 在此向frank123ya公開致歉                | 爆      | rainnawind   | 4/03  |
| (已被samhou6刪除) <ArtemXis> D1                  | 2       | -            | 4/03  |
| \[閒聊\] 本周LMS觀賽重點整理                     | 26      | InnGee       | 4/03  |
| \[閒聊\] HKE打不進季後賽之後該如何補強?          | 7       | a25270672    | 4/02  |
| \[閒聊\] 同人圖分享-海潮之音 娜米 Nami           | 3       | f222051618   | 4/02  |
| \[閒聊\] Gear是不是真的過譽了？                  | 25      | HomerEDLee   | 4/02  |
| \[閒聊\] 鐘老闆現在在想什麼?                     | 21      | brave0618    | 4/02  |
| \[電競\] LCL SPRING 2017-SEMIFINAL D2            | 2       | vic830710    | 4/02  |
| \[閒聊\] 最喜歡隊友選什麼角色                    | 15      | HAHEinthebar | 4/02  |
| (已被rainnawind刪除) <jumpballfan>Done           | 7       | -            | 4/02  |
| \[實況\] SKT T1 kkOma                            | 5       | narutodante  | 4/02  |
| \[揪團\] 秀造型NG團~ 關鍵字 -3 9:25              | 1       | main9        | 4/02  |
| \[實況\] 性感荷官 彈性積分/慎上路 關台           |         | MRsoso       | 4/02  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? | 53      | fkc          | 4/02  |
| \[電競\] 2017 LCS EU Spring W10D4 Final Day      | 60      | frank123ya   | 4/02  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? |         | a127         | 4/02  |
| \[閒聊\] 2017 LMS春季聯賽Highlight Reel 第三集   | 18      | Comebuy      | 4/02  |
| \[閒聊\] Gemini李星到底在幹嘛? 站著發呆10幾秒    |         | generalfungi | 4/02  |
| \[閒聊\] 為啥明明是他路差距卻都怪gear            | 7       | SanyaMyBride | 4/02  |
| \[閒聊\] HKE很愛炒短線?                          | 8       | China666     | 4/02  |
| \[公告\] LoL 樂透取消                            | 4       | \[彩券\]     | 4/02  |
| Re: \[問題\] 死不投降是不是台服素質如此差的原因? |         | loki5566     | 4/02  |

解釋爬蟲結果
------------

``` r
dim(frameAll)
```

    ## [1] 152   4

LOL眾多文章裡\[公告\] LoL 英雄聯盟板板規告和\[電競\] 近期賽事的文章， 就算日期是以前的文章，但仍然排在版面上。 還有當title欄位是本文已被刪除，那author欄位就會是空白的 author欄位rainnawind作者，每次發文回應人數都很熱門!

``` r
table(frameAll$title)
```

    ## 
    ##                   \n\t\t\t\n\t\t\t\t(本文已被刪除) [alive211079]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##    \n\t\t\t\n\t\t\t\t[公告] LoL 英雄聯盟板板規（Patch 17.01.01）\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##               \n\t\t\t\n\t\t\t\t[公告] LoL║英雄 ┌──┐４月閒聊區┌→\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[問題] LCK 飛斯 逆命 雷尼克頓\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t[問題] 請問丁特該不該回歸？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t[揪團] 快樂的恩居團(滿)\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                               \n\t\t\t\n\t\t\t\t[電競] 近期賽事 \n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[實況] Troll死你們 草人爬分台\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[實況] 晴時多雲偶陣雨 火龍果妹\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                           \n\t\t\t\n\t\t\t\tRe: [ANSI] 索娜 Sona\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##        \n\t\t\t\n\t\t\t\tRe: [閒聊] 新故事的汎根本是個碧曲吧！？\n\t\t\t\n\t\t\t 
    ##                                                                                2 
    ##                \n\t\t\t\n\t\t\t\t(已被samhou6刪除) <iloveykk> D1\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t(已被samhou6刪除) <starfishkira> D1\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [ex8338]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                               \n\t\t\t\n\t\t\t\t[ANSI] 索娜 Sona\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[問題] 招換師技能互換為何勝率會大增\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##             \n\t\t\t\n\t\t\t\t[問題] 清明節會有人幫阿姆姆掃墓嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t[問題] 最快打完前十場的方法\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##        \n\t\t\t\n\t\t\t\t[情報] 約德爾人的主題日！兒童節可愛優惠\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[閒聊] 台服現在最強寇格魔是誰?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                \n\t\t\t\n\t\t\t\t[閒聊] 為什麼Riot都不出多控英雄\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[閒聊] 球z跟丁特誰的JG比較強?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[閒聊] 新故事的汎根本是個碧曲吧！？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[實況] I3utterfly0v0/蝴蝶兒<3\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[實況] RPG Evi 韓服 日本隊上路\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                         \n\t\t\t\n\t\t\t\t[實況] SKT T1 kkOma(關\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                   \n\t\t\t\n\t\t\t\t[實況] 性感荷官 彈性積分五排\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##           \n\t\t\t\n\t\t\t\t[實況] 獸控實況主Dog4ni – 高端魔術秀\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##      \n\t\t\t\n\t\t\t\t[實況]麥麥貝比/今天適合練腳 練到105cm長腿\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##     \n\t\t\t\n\t\t\t\tRe: [閒聊] Apex回答太狂 還是大魚功力不足？\n\t\t\t\n\t\t\t 
    ##                                                                                6 
    ##                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [Aatrox5566]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [HITTEN]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [ooqr1995tw]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [sky082]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##   \n\t\t\t\n\t\t\t\t[心得] 真的很OP－野區暴徒 暴走重砲 吉茵珂絲 \n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[心得] 國動真的對積分現況有所改革了\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                                 \n\t\t\t\n\t\t\t\t[外絮] JCRE FB\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t[問題] 除了opgg有其他網站嗎\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                \n\t\t\t\n\t\t\t\t[問題] 會戰找不到自己游標怎麼辦\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t[揪團] 跟女友吵架的單雙（滿\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                       \n\t\t\t\n\t\t\t\t[閒聊] J特真的比動主播好\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##          \n\t\t\t\n\t\t\t\t[閒聊] LMS 2017 Spring 數據整理(~4/2)\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[閒聊] LOL有關於魔道的角色嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[閒聊] 在傳說啟程發現一件事情\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                \n\t\t\t\n\t\t\t\t[閒聊] 我在召喚峽谷裡得到了救贖\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                     \n\t\t\t\n\t\t\t\t[閒聊] 徵求LMS 4/8門票兩張\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[實況] TPS King / GodJJ 回來了\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t[影片] 歐洲最強逆命精華\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\tRe: [閒聊] 大家按Q技能會用小拇指嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                2 
    ##                       \n\t\t\t\n\t\t\t\t(本文已被刪除) [LIN6627]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [qwertytrew]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[問題] ARAM也有高低端場分別嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##              \n\t\t\t\n\t\t\t\t[問題] 丁特有考慮練蒙多醫生JG嗎？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##    \n\t\t\t\n\t\t\t\t[問題] 不投降跟風氣差 跟張家兄弟有什麼關係?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##         \n\t\t\t\n\t\t\t\t[問題] 殞落王者之劍是不是很適合特朗德?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                           \n\t\t\t\n\t\t\t\t[問題] 潘森是線霸嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[閒聊] HKE韓服成績真的深不可測\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##           \n\t\t\t\n\t\t\t\t[閒聊] WS如果要贏到底還缺了甚麼東西?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t[閒聊] 打野該積極gank嗎\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##        \n\t\t\t\n\t\t\t\t[閒聊] 國棟的鼻地戰術是傳承了中國武術？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                      \n\t\t\t\n\t\t\t\t[閒聊] 探討犽宿的風牆效用\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[閒聊] 解說記得的正宗中文教學\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                     \n\t\t\t\n\t\t\t\t[閒聊] 賈克斯打sup為啥不行\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                 \n\t\t\t\n\t\t\t\t[實況] FW NL / 煞氣o狂by衝崩銨\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                                \n\t\t\t\n\t\t\t\t[實況] M17 APEX\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##        \n\t\t\t\n\t\t\t\t[實況] 胡瓜太郎 Otofu 台服鑽二Sup遊玩中\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##       \n\t\t\t\n\t\t\t\tRe: [問題] 國動的崛起是否意味著lol走偏了\n\t\t\t\n\t\t\t 
    ##                                                                                4 
    ##                       \n\t\t\t\n\t\t\t\t(本文已被刪除) [asd0952]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [hongou]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                     \n\t\t\t\n\t\t\t\t(本文已被刪除) [melon1001]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [pttpig]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##         \n\t\t\t\n\t\t\t\t[外絮] Peanut安慰沒進入季後賽的Gorilla\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                          \n\t\t\t\n\t\t\t\t[揪團] 找上白金的夥伴\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                              \n\t\t\t\n\t\t\t\t[揪團] 金牌彈性-1\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                            \n\t\t\t\n\t\t\t\t[揪團] 銅銀小號雙排\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##         \n\t\t\t\n\t\t\t\t[閒聊] Apex回答太狂 還是大魚功力不足？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                   \n\t\t\t\n\t\t\t\t[閒聊] Weekly LCK Mic check \n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##       \n\t\t\t\n\t\t\t\t[閒聊] 如果實況界沒統神現在會是甚麼風氣?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##          \n\t\t\t\n\t\t\t\t[閒聊] 有沒有專精克雷德的玩家來交流個\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ## \n\t\t\t\n\t\t\t\t[閒聊] 會看EU&其他區比賽的人 是用什麼心情在看?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t[實況] 刺刺的 韓服 金三\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##               \n\t\t\t\n\t\t\t\t[實況] 藍色風暴 龍獸 金牌RANK~~~\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##         \n\t\t\t\n\t\t\t\t[影片]【國動】被戳到爆氣開啟動粉見面會\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ## \n\t\t\t\n\t\t\t\tRe: [問題] 死不投降是不是台服素質如此差的原因?\n\t\t\t\n\t\t\t 
    ##                                                                                8 
    ##   \n\t\t\t\n\t\t\t\tRe: [閒聊] 如果實況界沒統神現在會是甚麼風氣?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                       \n\t\t\t\n\t\t\t\t(本文已被刪除) [dant123]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                          \n\t\t\t\n\t\t\t\t[ANSI] 瓦羅然沒有派對\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##   \n\t\t\t\n\t\t\t\t[發錢] 國考放榜來猜猜灰鵝喜歡的LCK選手(Done)\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##     \n\t\t\t\n\t\t\t\t[閒聊] 【統神】深夜真性情—那些年的誤會委屈\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##      \n\t\t\t\n\t\t\t\t[閒聊] HKE vs. M17 G2 分析台+國人訪問逐字\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                       \n\t\t\t\n\t\t\t\t[閒聊] ROC是不是很悲情？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##           \n\t\t\t\n\t\t\t\t[閒聊] 一發死的角色是不是逐漸消失中?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                \n\t\t\t\n\t\t\t\t[閒聊] 大家按Q技能會用小拇指嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                          \n\t\t\t\n\t\t\t\t[閒聊] 小熊 Yuniko FB\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##       \n\t\t\t\n\t\t\t\t[閒聊] 同人圖分享-你以為有貓我就會推嗎？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##          \n\t\t\t\n\t\t\t\t[閒聊] 是不是應該拔除某些玩家的投票權\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                       \n\t\t\t\n\t\t\t\t[閒聊] 美板官方粉絲團 FB\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##    \n\t\t\t\n\t\t\t\t[電競] 2017 NA LCS夏季升降賽Day3 NV vs. GCU\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##         \n\t\t\t\n\t\t\t\tRe: [閒聊] LMS春季第一隊的上路會是誰？\n\t\t\t\n\t\t\t 
    ##                                                                                2 
    ##                       \n\t\t\t\n\t\t\t\tRe: [閒聊] 這季MVP該給誰\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##              \n\t\t\t\n\t\t\t\t(已被rainnawind刪除) <frank123ya>\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                \n\t\t\t\n\t\t\t\t(已被samhou6刪除) <ArtemXis> D1\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [AlzioNever]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                      \n\t\t\t\n\t\t\t\t(本文已被刪除) [FrogStar]\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                \n\t\t\t\n\t\t\t\t[公告] 在此向frank123ya公開致歉\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                        \n\t\t\t\n\t\t\t\t[公告] 樂透退盤處置說明\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##       \n\t\t\t\n\t\t\t\t[外絮] Kt Score:會拿出如粉絲所期待的表現\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##           \n\t\t\t\n\t\t\t\t[問題] 國動的崛起是否意味著lol走偏了\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##    \n\t\t\t\n\t\t\t\t[閒聊] M17要是5人同時醒著 能給前兩隊衝擊嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[閒聊] 四強的各路大家覺得強度比較？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                     \n\t\t\t\n\t\t\t\t[閒聊] 本周LMS觀賽重點整理\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##      \n\t\t\t\n\t\t\t\t[閒聊] 是不是只有進入遊戲畫面才知道ping值\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                          \n\t\t\t\n\t\t\t\t[閒聊] 恭喜M17 (已發)\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                           \n\t\t\t\n\t\t\t\t[閒聊] 這季MVP該給誰\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##    \n\t\t\t\n\t\t\t\t[實況] HKE KuKu / 口口口口口 跟韓國人定輸贏\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##       \n\t\t\t\n\t\t\t\t[實況] 獄胤天 清明時節雨紛紛 分分塊來RRR\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##              \n\t\t\t\n\t\t\t\tRe: [閒聊] Gear是不是真的過譽了？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##         \n\t\t\t\n\t\t\t\t(已被rainnawind刪除) <jumpballfan>Done\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                            \n\t\t\t\n\t\t\t\t[公告] LoL 樂透取消\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[揪團] 秀造型NG團~  關鍵字 -3  9:25\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t[揪團] 陪我一起打好不好(滿)\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##   \n\t\t\t\n\t\t\t\t[閒聊] 2017 LMS春季聯賽Highlight Reel 第三集\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                  \n\t\t\t\n\t\t\t\t[閒聊] Gear是不是真的過譽了？\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##    \n\t\t\t\n\t\t\t\t[閒聊] Gemini李星到底在幹嘛? 站著發呆10幾秒\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##          \n\t\t\t\n\t\t\t\t[閒聊] HKE打不進季後賽之後該如何補強?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                          \n\t\t\t\n\t\t\t\t[閒聊] HKE很愛炒短線?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##           \n\t\t\t\n\t\t\t\t[閒聊] 同人圖分享-海潮之音 娜米 Nami\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[閒聊] 為啥明明是他路差距卻都怪gear\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                    \n\t\t\t\n\t\t\t\t[閒聊] 最喜歡隊友選什麼角色\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                     \n\t\t\t\n\t\t\t\t[閒聊] 鐘老闆現在在想什麼?\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##      \n\t\t\t\n\t\t\t\t[電競] 2017 LCS EU Spring W10D4 Final Day\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##            \n\t\t\t\n\t\t\t\t[電競] LCL SPRING 2017-SEMIFINAL D2\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##                            \n\t\t\t\n\t\t\t\t[實況] SKT T1 kkOma\n\t\t\t\n\t\t\t 
    ##                                                                                1 
    ##           \n\t\t\t\n\t\t\t\t[實況] 性感荷官 彈性積分/慎上路 關台\n\t\t\t\n\t\t\t 
    ##                                                                                1

遇到節日，例如：兒童節、清明節，鄉民就會發關於lol廢文 最近eltar 發關於賽後訪問的文章，也非常熱門!!
