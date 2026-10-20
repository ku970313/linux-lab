Project 1

Q1

操作指令

cat daily.sh
bash daily.sh
ls
ls backup

執行過程

先用 cat 查看 daily.sh 的內容，再用 bash daily.sh 執行備份。

腳本裡的 cp 是把 261015.csv 複製到 backup 資料夾，mv 則是把檔案改名成 borrow_2026-10-15.csv。

執行結果

執行後用 ls 檢查，發現原本的 261015.csv 還在，backup 裡也有新增備份檔案，代表備份成功。

Q2

操作指令

ls backup
ls backup/*.csv | wc -l

執行過程

先用 ls backup 查看備份資料夾裡有哪些檔案，再用 wc -l 計算 CSV 檔案的數量。

執行結果

目前總共有 8 份備份，日期從 10/08 到 10/15。

今天的資料備份在 backup 資料夾裡，原本的檔名是 261015.csv，備份後改成 borrow_2026-10-15.csv。 

Q3

操作指令

awk 'FNR>1' backup/borrow_2026-10-*.csv | wc -l
awk -F',' 'FNR>1 {print $2}' backup/borrow_2026-10-*.csv | sort | uniq -c | sort -nr 

執行過程

先用 awk 排除每個 CSV 的標題，再用 wc -l 計算八天的借閱總次數。

接著取出讀者姓名，用 sort 和 uniq -c 統計每個人的借閱次數，最後按照次數由多到少排列。

執行結果

10/08 到 10/15 總共有 24 次借閱。

小美借了 12 次、小明 8 次、小華 4 次。

借閱最多的是小美，共 12 次。

Q4

操作指令

cat books.csv
cat reservations.csv
echo "2026-10-16,小明,B002" >> reservations.csv
cat reservations.csv

執行過程

先用 cat books.csv 查看書籍資料，找到 Linux 指令練習 的編號是 B002。

接著查看 reservations.csv，發現 10/16 沒有人預約 B002，所以可以幫小明預約。

用 echo 指令把小明的預約資料加進去，再用 cat 確認有沒有新增成功。

執行結果

成功幫小明預約 2026-10-16 的 Linux 指令練習，書籍編號是 B002，原本的預約紀錄也都還在。
