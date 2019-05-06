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
