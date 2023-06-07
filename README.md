# NLP_Champion

### 前置

使用環境Google Colab

使用程式碼 <<程式碼名>>

並將附屬資料夾NCKU-AICUP2023-baseline上傳到雲端硬碟的根目錄

### Part0

1.請確定drive.mount('/content/drive')有順利將雲端硬碟掛載

2.請執行cd /content/drive/MyDrive/NCKU-AICUP2023-baseline，並確保程式運作期間都在此資料夾內

3.請執行ls ，確保/content/drive/MyDrive/NCKU-AICUP2023-baseline內有資料夾/data (若是有資料缺少，請執行圖(1)的程式碼與指示，下載相關資料)

4.執行%pip install -r requirements.txt，安裝/content/drive/MyDrive/NCKU-AICUP2023-baseline/requirements.txt內所要求的函式庫


### Part1

1.執行 !pip install -U ckiptagger[tf,gdown]和data_utils.download_data_gdown("./")

2.請確保/content/drive/MyDrive/NCKU-AICUP2023-baseline/data內有檔案public_train.jsonl與private+public_test_data.jsonl，若是沒有可以從<<資料夾>>將資料放到/content/drive/MyDrive/NCKU-AICUP2023-baseline/data下

3.

4.

5.


### Part2

1. Use_Data_From_Part_1請填入4(for training與輸出預測結果)

2.確保/content/drive/MyDrive/NCKU-AICUP2023-baseline/data內有train_doc5_data4.jsonl、public_train.jsonl(經過dataset1與dataset2合併)、private+public_test_data.jsonl檔案和/wiki-pages資料夾(若是沒有可以從<<資料夾>>引入)

3.填入超參數

4.修改NEGATIVE_RATIO使得Label 0與Label 1樣本數相近

5.執行完程式碼2-3後會生成model

6.2-4中填入Part2模型名稱與路徑導入Part2模型，接著生成兩個檔案

7.2-5中選用檔案4，填入Part2模型名稱與路徑導入Part2模型，接著生成

### Part3
