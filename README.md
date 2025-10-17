# 2023 AI Cup NLP Contest (# 17/300)

### 前置

使用環境Google Colab

資源連結 : https://drive.google.com/drive/folders/1YROgftReHRzOV8TWCyQfqeixE9c0VET7?usp=sharing

使用程式碼 main_code/full_pipeline_final_season_Part1_(Bert)_5_31_(6)_already_test.ipynb

並將附屬資料夾(執行環境中的NCKU-AICUP2023-baseline)上傳到雲端硬碟的根目錄

### Part0

1.請確定drive.mount('/content/drive')有順利將雲端硬碟掛載

2.請執行cd /content/drive/MyDrive/NCKU-AICUP2023-baseline，並確保程式運作期間都在此資料夾內

3.請執行ls ，確保/content/drive/MyDrive/NCKU-AICUP2023-baseline內有資料夾/data (若是有資料缺少，請依照程式碼註解，下載相關資料)

4.執行%pip install -r requirements.txt，安裝/content/drive/MyDrive/NCKU-AICUP2023-baseline/requirements.txt內所要求的函式庫


### Part1

1.執行 !pip install -U ckiptagger[tf,gdown]和data_utils.download_data_gdown("./")

2.請確保/content/drive/MyDrive/NCKU-AICUP2023-baseline/data內有檔案public_train.jsonl與private+public_test_data.jsonl，若是沒有可以從<<資料夾>>將資料放到/content/drive/MyDrive/NCKU-AICUP2023-baseline/data下

3.

4.

5.


### Part2

1. Use_Data_From_Part_1請填入4 (for training與輸出預測結果)

2.確保/content/drive/MyDrive/NCKU-AICUP2023-baseline/data內有train_doc5_data4.jsonl、public_train.jsonl(經過dataset1與dataset2合併)、private+public_test_data.jsonl檔案和/wiki-pages資料夾

3.填入超參數 : Epoch 20,Batch_Size 64(Training與Test都是),Learning Rate 1e-05,Top 5,Sent_Seperate "yes",Comma "yes","Period" "no","Random_Choose" "yes",Prob_Limit 0.75, Testing_or_not "no"

4.修改NEGATIVE_RATIO使得Label 0與Label 1樣本數相近 (大約0.115)

5.[訓練]接著執行2-2,2-3-2後會生成model (2-3-1可以跳過)

6.[生成下一階段資料]2-4中填入Part2模型名稱(ckpt_name)「F1_0.7573400417066631_Precision0.7638888888888888_model.2670.pt」與路徑(CKPT_DIR)「checkpoints/sent_retrieva/e20_bs64_1e-05_neg0.115_top5_data4_prob0.75_yes_yes_no_yes」導入Part2訓練好的模型，接著生成兩個檔案(Train) :  train_doc5sent5_data4_e20_bs64_1e-05_neg0.1096_top5_data4_prob0.75_yes_yes_no_yes.jsonl與(Valid) :  dev_doc5sent5_data4_e20_bs64_1e-05_neg0.1096_top5_data4_prob0.75_yes_yes_no_yes.jsonl

7.[測試]2-5中Data_From_Part_1_Test填入4，填入Part2模型名稱(ckpt_name)「F1_0.7573400417066631_Precision0.7638888888888888_model.2670.pt」與路徑(DIR_FOR_MODEL)「checkpoints/sent_retrieva/e20_bs64_1e-05_neg0.115_top5_data4_prob0.75_yes_yes_no_yes」導入Part2模型，接著生成下一階段的Testing檔案「test_doc5sent5_data4_e20_bs64_1e-05_neg0.115_top5_data4_prob0.75_yes_yes_no_yes.jsonl」

### Part3

1. Use_Data_From_Part_1請填入4 (for training與輸出預測結果)，Par2_Number_of_Sent = "5"，Part2_Model_Path = "checkpoints/sent_retrieval/e20_bs64_1e-05_neg0.115_top5_data4_prob0.75_yes_yes_no_yes"，SEP_NUMBER = 0

2.確保/content/drive/MyDrive/NCKU-AICUP2023-baseline/data內有train_doc5sent5_data4_e20_bs64_1e-05_neg0.1096_top5_data4_prob0.75_yes_yes_no_yes.jsonl與(Valid) :  dev_doc5sent5_data4_e20_bs64_1e-05_neg0.1096_top5_data4_prob0.75_yes_yes_no_yes.jsonl檔案

3.[訓練]填入超參數 : Epoch 20,Batch_Size 24(Training與Test都是),Learning Rate 1e-05,MAX_SEQ_LEN 256,EVIDENCE_TOPK 5，接著執行3-2,3-3-2後會生成model (3-3-1可以跳過)

7.[測試]Use_Data_From_Part_1請填入4 (for training與輸出預測結果)，Par2_Number_of_Sent = "5"，Part2_Model_Path = "checkpoints/sent_retrieval/e20_bs64_1e-05_neg0.115_top5_data4_prob0.75_yes_yes_no_yes"，EVIDENCE_TOPK = 5，CKPT_DIR = "checkpoints/claim_verification/e20_bs25_1e-05_top5_data4_SEP0" ,MODEL_NAME = bert-base-chinese,ckpt_name = val_acc=0.5895_model.2280.pt,

8.確認檔案./data/test_doc5sent5_data4_e20_bs64_1e-05_neg0.115_top5_data4_prob0.75_yes_yes_no_yes.jsonl存在，並執行完3-4，得到檔案submission_e20_bs64_1e-05_neg0.1096_top5_data4_prob0.75_yes_yes_no_yes.jsonl


