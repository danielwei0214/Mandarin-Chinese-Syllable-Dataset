# Mandarin Chinese Syllable Dataset

汉语普通话音节数据集 - 覆盖性广，使用频率高，涵盖所有普通话发音。

---

## 数据集介绍

本数据集专为汉语普通话发音唇形评估设计，适用于如数字人唇形训练和优化等场景，同时也包括详细的音节词典，为语言学研究提供了重要资源。数据集包含覆盖率广泛的《现代汉语词典》和普通话常用词词典，并且测试集覆盖了所有标准汉语普通话音节，排除方言、声调、音变和生僻字等特殊情况。数据集大小控制在1,000至2,000字之间，以节约资源。

## 数据集用途

1. **唇形识别和训练**：该数据集主要用于普通话唇形识别系统的训练和评估，特别适用于数字人的唇形同步训练和优化。通过覆盖所有标准的普通话音节，该数据集可以有效帮助模型学习和识别普通话中所有可能出现的唇形变化。

2. **文本生成与语音合成**：数据集提供的音节和词语可以用于训练生成模型，实现高质量的文本生成与语音合成。通过对拼音的准确标注，确保生成的文本和语音能够精确对应。

3. **语言学研究**：该数据集也可用于语言学研究，尤其是涉及音节覆盖率、词频统计和拼音转换的研究工作。它为普通话音节的全面覆盖提供了一个有价值的参考。

   ......

## 文件描述

| 文件名 | 描述 | 大小 |
| ------ | ---- | ---- |
| Mandarin 206 Words (Covering All Syllables).txt | 包含206个普通话词语，覆盖除生僻字、方言音和多音字（如嗯、咯、谁、这）以外的所有音节。 | 小 |
| Mandarin Chinese syllables (excluding tones).txt | 列出不含声调的所有418个音节。 | 小 |
| Mandarin Syllable Dictionary.json | 包含按音节类型分类的普通话音节词典，使用频率高。 | 中 |
| Modern Chinese Syllable Dictionary.json | 包含按音节类型分类的《现代汉语词典》第7版中所有词语，覆盖率最高。 | 大 |
| test.json | 完整句子，包含1,713个音节，音节覆盖率达100%（排除生僻字、方言音和多音字）。 | 小 |
| test.txt | 包含test.json文件中的文本内容。 | 小 |

## 数据集格式说明

### test.json 格式说明
- 总音节数量: 1713个
- 音节覆盖率：100.00%，除去只有一个生僻字的音节，方言音，多音字（嗯、咯、谁、这）的情况。
- 未覆盖的音节（指有且只有一个字的音节）:
- {'ň', 'cei', 'tei', 'ňg', 'chua', 'hng', 'lo', 'nun', 'zhei', 'nou', 'hm', 'ń', 'kei', 'den', 'rua', 'dia', 'ńg', 'eng', 'shei'}
  - 生僻字（7个）：鞥（eng）；挼（rua）；𤭢（cei）；黁（nun）；噷（hm）；耨（nou）；歘（chua）
  - 多音字（8个）：'shei'【谁（shui）】的又音；'lo'【咯（ge）】的又音；'ň'，'ń'，'ňg'， 'ńg'，'hng'【嗯】的又音；'zhei'【这（zhe）】的又音
  - 方言音（4个）：嗲（dia）；扽（den）；剋（kei）；忒（tei）
    
```json
{
  "words": ["迸发", "抖擞", "晒", "不胫而走", "辩护人", "金龟子"],  # 包含音节的词语
  "text": "辩护人在法庭上激情迸发，为客户抖擞精神；案件详情不胫而走，社会各界关注。外面的金龟子在阳光下晒得慵懒。",  # 大模型根据词语生成的文本
  "pinyin": "bian hu ren zai fa ting shang ji qing beng fa ， wei ke hu dou sou jing shen ； an jian xiang qing bu jing er zou ， she hui ge jie guan zhu 。 wai mian de jin gui zi zai yang guang xia shai de yong lan 。"  # text文本所对应的拼音（不含声调）
}
```


### Modern Chinese Syllable Dictionary.json/Mandarin Syllable Dictionary.json 数据格式说明
- **Modern Chinese Syllable Dictionary.json/现汉音节词典**：包括《现代汉语词典》第7版的所有词语，按音节类型进行归类，覆盖率最高，70000+条词语。
- **Mandarin Syllable Dictionary.json/普通话音节词典**：包括普通话中最常用的词语，按音节类型进行了归类，使用频率最高，16000+个词语。

```json
[
  {
    "id": "0001",      # 音节序号
    "syllable": "a",   # 音节详情
    "words": ["阿", "阿姨"],  # 包含此音节的词语
    "pinyin": ["a", "a yi"]  # 词语所对应的拼音
  },
  ...
]
```

## 数据集优势

1. **高效覆盖与资源优化**：尽管排除了生僻字、方言音和多音字，该数据集通过高效选择常用词语，在有限的资源内实现了对标准普通话音节的全面覆盖。这种方式不仅节省了数据集的构建成本，还确保了训练模型时的资源高效利用。

2. **实际应用性强**：数据集基于普通话最常用词语构建，覆盖了最常见的音节类型，这意味着其在实际应用中的效果更好，能够更准确地反映普通话的使用情况。对于需要高效训练和快速部署的模型，这样的数据集可以显著提升模型的实际表现。

3. **灵活性与可扩展性**：由于数据集中的词语选择具有一定的灵活性，并且通过大语言模型支持随机生成文本内容，因此可以根据不同的需求扩展或定制化，满足多样化的应用场景，如不同的语音识别环境或唇形识别精度要求。

4. **拼音与文本对齐**：提供的拼音与文本严格对齐，使得在后续的语音合成、文本转语音(TTS)以及语音识别(ASR)模型训练中能够准确地进行发音和唇形的学习，从而提升模型的输出质量。

## 数据集构建流程

![Mandarin Chinese Syllable Dataset Flowchart](https://github.com/danielwei0214/Mandarin-Chinese-Syllable-Dataset/blob/main/Mandarin%20Chinese%20Syllable%20Dataset%20Flowchart.png)

### 附：方案二流程
1. 初始化音节集合：首先列出所有需要覆盖的音节，形成一个音节集合【汉语普通话音节（不含声调）418个】。
2. 选择能覆盖最多音节的词语：每一步中查找能覆盖最多“尚未覆盖音节”的词语。所谓“尚未覆盖音节”是指还没有被任何已选词语覆盖的音节。
3. 更新音节集合：一旦选择了一个词语，就从“尚未覆盖音节”的集合中移除该词语覆盖的音节。
4. 重复选择过程：继续重复这个过程，每次都从剩余的“尚未覆盖音节”集合中选择一个能覆盖最多音节的词语，直到所有音节都被覆盖或者没有更多的词语可以增加覆盖的音节数量。
通过这个方法，能够确保用最少的词语覆盖所有不同的音节，而且每次选择都是基于目前尚未覆盖的音节来最大化覆盖效率。


### 附：大模型数据生成Prompt
- 根据“角色 + 任务（详情）+ 目标 + 格式/内容要求 + 示例”的模板创建提示词。‘角色’界定了LLMs的角色，‘任务’说明了具体的任务背景和细节，‘目标’是模型应输出的结果，而格式/内容要求则规定了输出的具体形式。
- 思维链技术（CoT）使LLMs通过模拟人类解题思维，有效地处理复杂任务并展现出类似人类的推理能力，从而提升问题解决的效率和准确度；
- 少样本学习技术（Few_shot Learning）则通过分析有限的示例，使这些模型能迅速学习并适应新的任务。
- 这个过程是迭代的，通过反复测试和评估模型输出，不断调整提示词以获取稳定的结果。
  
```json
prompt = f"""

 你是一个中文语言学家和高级写作专家，擅长限制性中文写作，直到达到最高的中文语言水平。
 
 请你使用下面列表中的词语一步步进行思考写作，
 首先了解每个词语的语义，思考其出现的上下文语境；其次找到所有词语的显式或隐含联系（词性，主题，范围等）；最后参考示例，根据语义及联系，逐步思考将所有词语融合到一段话中；确保符合中文表达习惯，避免用词不当，没有语法错误，表达自然流畅。
 要求必须包含列表中的所有词语，每个词语仅使用一次，不要重复使用，长度要求50个汉字字符左右。
 示例：{{"words":["山村", "万籁俱寂", "咯吱", "簌簌","枯枝","偶尔","冬天","落"],"text":"冬天的山村，到了夜里就万籁俱寂，只听得雪花簌簌地不断往下落，树木的枯枝被雪压断了，偶尔咯吱一声响。"}}
 
 词语：```{selected_words}
 
 注意：只能输出json格式内容，包含words和text键值，不能输出其他无关内容。"""
```

### 附：数据集质量检验流程
- 目标：检验词语/段落文本所对应音节是否覆盖汉语所有音节类型
- 指标：总音节数量、覆盖的音节种类数量、音节覆盖率、未覆盖音节种类、各音节频率
- 流程：
1. 输入：汉语普通话音节（不含声调、音变）418个（txt）；待检验词语/段落文本文件（txt,json）
2. 读取词语\段落文本文件
3. 读取汉语普通话音节（不含声调、音变）418个文本文件
4. 使用pypinyin库对词语\段落文本进行音节标注，将结果存为列表
5. 对拼音进行标准化处理，例如将特殊的字符“ü”转换为“v”。
6. 使用collections库中的counter统计总音节数量、覆盖的音节种类数量、音节覆盖率、未覆盖音节种类、各音节频率
7. 输出结果：检验词语/段落文本的总音节数量、覆盖的音节种类数量、音节覆盖率、未覆盖音节种类、各音节频率

## 许可证和引用声明

**许可证**

本数据集使用 [CC BY-NC 4.0 许可证](https://creativecommons.org/licenses/by-nc/4.0/)进行分发。您可以自由使用和分享数据集，但需注明出处，并且仅限于非商业用途。

**引用声明**

如果您在研究或其他项目中使用了“汉语普通话音节数据集”，请注明数据集的来源，并使用以下引用格式：

```markdown
汉语普通话音节数据集 | Mandarin Chinese Syllable Dataset:  
https://github.com/danielwei0214/Mandarin-Chinese-Syllable-Dataset
```
通过适当的引用，您帮助我们提升数据集的影响力并支持进一步的研究与开发。  

## 致谢

在制作“汉语普通话音节数据集”的过程中，我们使用了 [《现代汉语词典》第七版数据库](https://github.com/CNMan/XDHYCD7th) 提供的数据资源。在此，我们对相关数据的贡献者表示衷心的感谢。  

---


# Mandarin Chinese Syllable Dataset

Mandarin Chinese Syllable Dataset - Extensive coverage, high frequency of use, and includes all Mandarin pronunciations.

---

## Dataset Introduction

This dataset is specifically designed for evaluating lip movements in Mandarin Chinese pronunciation. It is applicable to scenarios such as lip movement training and optimization for digital humans and also includes a detailed syllable dictionary, providing an important resource for linguistic research. The dataset includes widely covered dictionaries like the "Modern Chinese Dictionary" and commonly used Mandarin word dictionaries. The test set covers all standard Mandarin syllables, excluding dialects, tones, tone sandhi, and rarely used characters. The dataset size is controlled between 1,000 to 2,000 characters to conserve resources.

## Dataset Uses

1. **Lip Movement Recognition and Training**: This dataset is primarily used for training and evaluating lip movement recognition systems for Mandarin, especially suited for lip sync training and optimization of digital humans. By covering all standard Mandarin syllables, the dataset effectively helps models learn and recognize all possible lip movement variations in Mandarin.

2. **Text Generation and Speech Synthesis**: The syllables and words provided by the dataset can be used to train generative models, enabling high-quality text generation and speech synthesis. Accurate pinyin annotations ensure that the generated text and speech correspond precisely.

3. **Linguistic Research**: The dataset can also be used in linguistic research, particularly in studies involving syllable coverage, word frequency statistics, and pinyin conversion. It provides a valuable reference for comprehensive coverage of Mandarin syllables.

---

## File Description

| Filename | Description | Size |
| -------- | ----------- | ---- |
| Mandarin 206 Words (Covering All Syllables).txt | Contains 206 Mandarin words covering all syllables except for rare characters, dialect pronunciations, and polyphonic characters (e.g., 嗯, 咯, 谁, 这). | Small |
| Mandarin Chinese syllables (excluding tones).txt | Lists all 418 syllables without tones. | Small |
| Mandarin Syllable Dictionary.json | Includes a dictionary of Mandarin syllables categorized by syllable type, with high frequency of use. | Medium |
| Modern Chinese Syllable Dictionary.json | Includes all words from the 7th edition of the "Modern Chinese Dictionary," categorized by syllable type, with the highest coverage. | Large |
| test.json | Complete sentences containing 1,713 syllables, with 100% syllable coverage (excluding rare characters, dialect pronunciations, and polyphonic characters). | Small |
| test.txt | Contains the text content from the test.json file. | Small |

---

## Dataset Format Description

### test.json Format Description
- Total number of syllables: 1713
- Syllable coverage: 100.00%, excluding syllables with only one rare character, dialect pronunciations, and polyphonic characters (e.g., 嗯, 咯, 谁, 这).
- Uncovered syllables (syllables with only one corresponding character):
  - {'ň', 'cei', 'tei', 'ňg', 'chua', 'hng', 'lo', 'nun', 'zhei', 'nou', 'hm', 'ń', 'kei', 'den', 'rua', 'dia', 'ńg', 'eng', 'shei'}
    - Rare characters (7): 鞥 (eng); 挼 (rua); 𤭢 (cei); 黁 (nun); 噷 (hm); 耨 (nou); 歘 (chua)
    - Polyphonic characters (8): Alternate pronunciations of 'shei' (who - shui); 'lo' (咯 - ge); 'ň', 'ń', 'ňg', 'ńg', 'hng' (嗯); 'zhei' (这 - zhe)
    - Dialect pronunciations (4): 嗲 (dia); 扽 (den); 剋 (kei); 忒 (tei)

```json
{
  "words": ["迸发", "抖擞", "晒", "不胫而走", "辩护人", "金龟子"],  # Words containing the syllables
  "text": "辩护人在法庭上激情迸发，为客户抖擞精神；案件详情不胫而走，社会各界关注。外面的金龟子在阳光下晒得慵懒。",  # Text generated by a large model based on the words
  "pinyin": "bian hu ren zai fa ting shang ji qing beng fa ， wei ke hu dou sou jing shen ； an jian xiang qing bu jing er zou ， she hui ge jie guan zhu 。 wai mian de jin gui zi zai yang guang xia shai de yong lan 。"  # Pinyin corresponding to the text (without tones)
}
```

### Modern Chinese Syllable Dictionary.json/Mandarin Syllable Dictionary.json Format Description
- **Modern Chinese Syllable Dictionary.json**: Includes all words from the 7th edition of the "Modern Chinese Dictionary," categorized by syllable type, with the highest coverage, over 70,000 entries.
- **Mandarin Syllable Dictionary.json**: Includes the most commonly used words in Mandarin, categorized by syllable type, with the highest frequency of use, over 16,000 entries.

```json
[
  {
    "id": "0001",      # Syllable sequence number
    "syllable": "a",   # Syllable details
    "words": ["阿", "阿姨"],  # Words containing this syllable
    "pinyin": ["a", "a yi"]  # Pinyin corresponding to the words
  },
  ...
]
```

---

## Dataset Advantages

1. **Efficient Coverage and Resource Optimization**: Despite excluding rare characters, dialect pronunciations, and polyphonic characters, this dataset achieves comprehensive coverage of standard Mandarin syllables through efficient selection of commonly used words. This approach not only reduces the cost of dataset construction but also ensures efficient resource utilization during model training.

2. **Practical Application**: The dataset is constructed based on the most commonly used Mandarin words, covering the most frequent syllable types. This means it performs better in practical applications, more accurately reflecting the usage of Mandarin. For models that require efficient training and rapid deployment, this dataset can significantly enhance performance.

3. **Flexibility and Scalability**: The selection of words in the dataset is flexible, and with support from large language models for random text generation, it can be expanded or customized according to different needs, meeting various application scenarios, such as different speech recognition environments or lip movement recognition accuracy requirements.

4. **Alignment of Pinyin and Text**: The provided pinyin is strictly aligned with the text, allowing for accurate pronunciation and lip movement learning in subsequent speech synthesis, text-to-speech (TTS), and automatic speech recognition (ASR) model training, thereby improving the quality of model output.

---

## Dataset Construction Process

![Mandarin Chinese Syllable Dataset Flowchart](https://github.com/danielwei0214/Mandarin-Chinese-Syllable-Dataset/blob/main/Mandarin%20Chinese%20Syllable%20Dataset%20Flowchart.png)

### Appendix: Alternative Process Flow
1. Initialize the Syllable Set: First, list all the syllables that need to be covered, forming a syllable set [Mandarin Chinese syllables (excluding tones) 418 syllables].
2. Select Words that Cover the Most Syllables: In each step, find the word that covers the most “uncovered syllables.” “Uncovered syllables” refer to syllables that have not been covered by any selected word.
3. Update the Syllable Set: Once a word is selected, remove the syllables covered by that word from the “uncovered syllables” set.
4. Repeat the Selection Process: Continue this process, selecting a word that covers the most syllables from the remaining “uncovered syllables” set each time until all syllables are covered or no more words can add to the coverage.

This method ensures that all different syllables are covered with the fewest words, and each selection is based on maximizing coverage efficiency for the remaining uncovered syllables.

### Appendix: Large Model Data Generation Prompt
- Create prompts using the template “Role + Task (Details) + Goal + Format/Content Requirements + Example.” ‘Role’ defines the LLM’s role, ‘Task’ describes the specific task background and details, ‘Goal’ specifies the model’s expected output, and Format/Content Requirements define the specific format of the output.
- Chain-of-Thought (CoT) technology enables LLMs to process complex tasks by simulating human problem-solving thinking, improving efficiency and accuracy in problem-solving.
- Few-shot learning technology allows these models to quickly learn and adapt to new tasks by analyzing limited examples.
- This process is iterative, with repeated testing and evaluation of model outputs, constantly adjusting the prompt to achieve stable results.

```json
prompt = f"""

 你是一个中文语言学家和高级写作专家，擅长限制性中文写作，直到达到最高的中文语言水平。
 
 请你使用下面列表中的词语一步步进行思考写作，
 首先了解每个词语的语义，思考其出现的上下文语境；其次找到所有词语的显式或隐含联系（词性，主题，范围等）；最后参考示例，根据语义及联系，逐步思考将所有词语融合到一段话中；确保符合中文表达习惯，避免用词不当，没有语法错误，表达自然流畅。
 要求必须包含列表中的所有词语，每个词语仅使用一次，不要重复使用，长度要求50个汉字字符左右。
 示例：{{"words":["山村", "万籁俱寂", "咯吱", "簌簌","枯枝","偶尔","冬天","落"],"text":"冬天的山村，到了夜里就万籁俱寂，只听得雪花簌簌地不断往下落，树木的枯枝被雪压断了，偶尔咯吱一声响。"}}
 
 词语：```{selected_words}
 
 注意：只能输出json格式内容，包含words和text键值，不能输出其他无关内容。"""
```

## License and Citation

**License**

This dataset is distributed under the [CC BY-NC 4.0 License](https://creativecommons.org/licenses/by-nc/4.0/). You are free to use and share the dataset, provided that you give appropriate credit and use it only for non-commercial purposes.

**Citation**

If you use the “Mandarin Chinese Syllable Dataset” in your research or projects, please acknowledge the source using the following citation format:

```markdown
Mandarin Chinese Syllable Dataset:  
https://github.com/danielwei0214/Mandarin-Chinese-Syllable-Dataset
```

Proper citation helps us increase the dataset’s impact and supports further research and development.


## Acknowledgments

We extend our sincere thanks to the contributors of the [Modern Chinese Dictionary (7th Edition) Database](https://github.com/CNMan/XDHYCD7th) for providing valuable data resources used in creating the "Mandarin Chinese Syllable Dataset." Your contributions have been instrumental in making this dataset a comprehensive resource for linguistic research and technological development.
