CHED_data

————触发词识别任务数据
## 文件列表：
doc2id.jsonl #文档 ID 映射文件
fine_grained_labels.jsonl #细粒度事件标签文件
train.jsonl #训练集数据
valid_text_only_data.jsonl #验证集无答案文本数据
valid.jsonl #验证集数据

## 数据集格式说明：
{
  "sen_id": 7562,  #句子序号
  "doc_id": 32035,   #文档编码
  "text": "进军建德，擒贼帅赵桑干。",  #文本内容
  "events": [  #事件列表，包含以下字段：
    {
      "id": 12970,  #标签序号
      "trigger": "进军",  #触发词文本
      "label": "军事-备战-出兵",  #使用细粒度标签
      "start_offset": 0,   #触发词在“text”中的起始索引位置
      "end_offset": 2  #触发词在“text”中的终止索引位置
    },
    {
      "id": 12971,
      "trigger": "擒",
      "label": "军事-作战-俘虏",
      "start_offset": 5,
      "end_offset": 6
    }
  ]
}


————细粒度事件判定任务数据##与“触发词识别任务数据”相同
## 文件列表：
doc2id.jsonl #文档 ID 映射文件
fine_grained_labels.jsonl #细粒度事件标签文件
train.jsonl #训练集数据
valid_text_only_data.jsonl #验证集无答案文本数据
valid.jsonl #验证集数据

## 数据集格式说明：
{
  "sen_id": 7562,  
  "doc_id": 32035,   
  "text": "进军建德，擒贼帅赵桑干。", 
  "events": [  
    {
      "id": 12970,  
      "trigger": "进军",  
      "label": "军事-备战-出兵",  #使用细粒度标签
      "start_offset": 0,   
      "end_offset": 2  
    },
    {
      "id": 12971,
      "trigger": "擒",
      "label": "军事-作战-俘虏",
      "start_offset": 5,
      "end_offset": 6
    }
  ]
}


————粗粒度事件类型判定任务数据
## 文件列表：
doc2id.jsonl #文档 ID 映射文件（与细粒度相同）
coarse_grained_labels.jsonl #粗粒度事件标签文件
train_coarse.jsonl #粗粒度训练集数据
valid_text_only_data.jsonl #验证集无答案文本数据（与细粒度相同）
valid_coarse.jsonl #粗粒度验证集数据

## 数据集格式说明：
{
  "sen_id": 2191,
  "doc_id": 32030,
  "text": "己丑，太尉张禹免。",
  "events": [
    {
      "id": 3653,
      "trigger": "免",
      "label": "职位",   #使用粗粒度标签
      "start_offset": 7,
      "end_offset": 8
    }
  ]
}