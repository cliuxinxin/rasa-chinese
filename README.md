# 跑出英文的对话系统
OK
# 加上中文的spacy模型
从这里下载
https://eyun.baidu.com/s/3ggH5o4r
安装
pip install zh_core_web_sm-2.x.x.tar.gz
# 修改成为中文的对话系统
rasa-moodbot-demo-complete
这个文档就是具体的实现
nlu_md : 维护intents
stories_md ： 维护stories
domain_yml ： 维护domain
维护好这几个文档，就能实现自己的对话了
# have fun
# 详细讲解
intents
发起对话的人的目的
intent:greet
- 嘿，我是[小王](PERSON)
- 你好，我是[张三](PERSON)
- 你吃饭了吗，我是[小红](PERSON)
- 你好
你好的intent，几个例子，还可以设定实体
stories
对话的走向
happy path               <!-- name of the story - just for debugging -->
* greet              
  - utter_greet
* mood_great               <!-- user utterance, in format intent[entities] -->
  - utter_happy
* mood_affirm
  - utter_happy
* mood_affirm
  - utter_goodbye
这是一条happy路线，双方是如何对话的
domain
具体的对话内容 
intents:
- greet
- goodbye
- mood_affirm
- mood_deny
- mood_great
- mood_unhappy

slots:
  img_api_response:
    type: unfeaturized

actions:
- utter_greet
- utter_cheer_up
- utter_did_that_help
- utter_happy
- utter_goodbye
- utter_unclear
- __main__.ApiAction

templates:
  utter_greet:
  - text: "嘿，你感觉怎么样?"

  utter_cheer_up:
  - text: "你看了可能会感觉不错: {img_api_response}"

写明intents，actions，还可以插入python动作。
然后丢入文件就能训练了

以下是原来的文档可以自己看，也可以忽略
# Conversational AI with Rasa NLU and Core
Demo application for the PyData Conference in Amsterdam 2018

You can find the slides for the presentation at [Slideshare](https://www.slideshare.net/TomBocklisch/conversational-ai-with-rasa-pydata-workshop-98683172).

## Installation
The notebooks contain the installation instructions as their first step. Basically,
you'll need a virtualenv with `rasa_core`, `rasa_nlu[spacy]` and `spacy` installed.

Also make sure to install a spacy language model for `en`.

## Notebooks
- `rasa-moodbot-demo-starter` this is what we are going to start with
- `rasa-moodbot-demo-complete` this is how our notebook should look like once we are done
- `rasa-moodbot-demo-complete-executed` if hell breaks loose, this is a backup notebook with all the output cells filled

The additional files (`nlu.md`, `stories.md`, `domain.yml`, `config.yml`, `story_eval.pdf`, `story_graph.png`)
will be explained and created in the notebooks.

Once you ran the notebooks, there should be a `models/` folder containing your trained Rasa model.

## Additional Material

### Running duckling locally
- run the duckling docker container
	```bash
	docker run -p 8000:8000 rasa/duckling
	```

- add the duckling component to your pipeline:
	```yaml
	- name: "ner_duckling_http"
	  url: localhost:8000
	```

## Slides
TBC - I'll add the slides once the talk is done 
