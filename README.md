# TraGe

We provide a rapid implementation of TraGe to facilitate future research.

## 1. Requirements
```
Python >= 3.6
CUDA: 11.4
torch >= 1.1
six >= 1.12.0
scapy == 2.4.4
numpy == 1.19.2
shutil, random, json, pickle, binascii, flowcontainer, argparse, packaging, tshark
```

## 2. Traffic Pre-processing

We need to manually specify the number of categories (i.e., class_num) and the random seed (i.e., random_seed) for random sampling.

```
python3 pre-process/run_process.py \
        --pcap_path path_to_raw_dataset/pcap/ \
        --dataset_dir path_to_processed_dataset/datasets/ \
        --middle_save_path path_to_processed_dataset/result/ \
        --class_num 10 \
        --random_seed 01
```


## 3. Model Fine-tuning

You can use TraGe directly by downloading the [pre-trained TraGe model](https://drive.google.com/file/d/1eb-EIkWyLv3tD7wEzJC5Gx1aU57gOY-h/view?usp=drive_link).

```
CUDA_VISIBLE_DEVICES=0 python3 finetune/run_classifier.py \
        --pretrained_model_path path_to_pretrained_model/pretrained_models.bin \
        --output_model_path path_to_finetuned_model/finetuned_model.bin \
        --vocab_path models/encryptd_vocab.txt \
        --config_path models/bert/base_config.json \
        --train_path path_to_processed_dataset/datasets/train_dataset.tsv \
        --dev_path path_to_processed_dataset/datasets/valid_dataset.tsv \
        --test_path path_to_processed_dataset/datasets/test_dataset.tsv \
        --epochs_num 10 \
        --batch_size 32 \
        --labels_num 10
```

## 4. Citation

If you are using the work in TraGe for academic work, please cite the paper:

```
@inproceedings{lin2025trage,
  title={TraGe: A Generic Packet Representation for Traffic Classification Based on Header-Payload Differences},
  author={Lin, Chungang and Jiang, Yilong and Zhang, Weiyao and Meng, Xuying and Zuo, Tianyu and Zhang, Yujun},
  booktitle={2025 IEEE/ACM 33rd International Symposium on Quality of Service (IWQoS)},
  pages={1--6},
  year={2025},
  organization={IEEE}
}
```
