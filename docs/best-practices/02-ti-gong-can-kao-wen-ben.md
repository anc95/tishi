# 📚 提供参考文本

GPT在回答一些深奥主题或需要引用网址的问题时，可能会胡说八道编造虚假答案。这时你可以为 GPT 提供参考文本可以帮助它们在回答问题时减少捏造内容。

{% hint style="info" %}
当你初次阅读时，你可能会觉得以下两种方式是一样的。其实，这两种策略虽然都是提供参考文本给GPT，但他们的使用方式和目的有所不同。前者更侧重于让模型理解并使用参考文本中的信息再结合GPT的知识库进行回答，而后者则更侧重于让模型直接引用参考文本中的内容进行回答。
{% endhint %}

## 使用参考文本指导模型的答案

如果我们能为模型提供与当前查询相关的可靠信息，那么我们可以指示模型利用所提供的信息来撰写答案。&#x20;

提示语结构：

```
请使用由三引号分隔的提供的文章来回答问题。如果答案不能在文章中找到，请回答 "我无法找到答案。"
"""文章1"""
"""文章2"""
"""文章3"""

我的问题：<在此处插入问题>
```

提示语示例：


```
请使用以下三引号分隔的文章回答问题。如果答案无法在文章中找到，请写“无法找到答案”。

"""
什么是「小语 GPT」？
小语 GPT 所提供的内容生成功能所接入的服务提供商为微软的 Azure OpenAI 服务，支持用户轻松访问 GPT-3.5 和 GPT-4 模型。这些模型可以轻松适应特定的任务，包括但不限于内容生成、汇总、语义搜索和自然语言到代码的转换。
目前微软的 Azure OpenAI 服务仅面向企业客户提供，这是目前国内合法使用 OpenAI 服务的唯一途径。提示语科技（北京）有限公司目前已经获得微软授权。
"""
"""
比较小语 GPT、Azure OpenAI 和 OpenAI
相较于其它生成性模型，OpenAI 的 GPT 模型具有显著的潜在优势。然而，若不经过精心设计并采纳全面的缓解措施，这类模型可能产生错误甚至有害的内容。
Azure OpenAI 服务通过 OpenAI GPT-3.5、GPT-4 和 DALL-E 模型为企业客户提供高级语言 AI，更加关注实用安全性。借助Azure OpenAI，企业客户在运行与OpenAI 相同的模型时可获得 Microsoft Azure 的安全功能。 
在保留了 OpenAI 的 GPT 强大生成能力和 Azure OpenAI 服务安全功能的基础上，小语 GPT 针对国内政策对内容生成实施了更严格的规范，包括但不限于遵守法律法规、尊重社会公德、维护公序良俗，体现社会主义核心价值观、防止歧视性内容、避免不公平竞争、防止虚假信息传播，以及不侵犯他人肖像、隐私、知识产权等权益。
"""

问题：小语 GPT 是提示语科技自研的吗？
```


<figure><img src="/images/image-28.png" alt="" /><figcaption></figcaption></figure>

## **指导模型使用参考文本中的引文来回答**

如果输入内容已经给出了一些相关的背景知识，那么我们可以直接要求GPT通过引用文档中的内容来增强它的回答。 这里有一个小技巧，我们可以通过一种特殊格式来标注引用的内容，以便于检查输出中的引用是否准确

提示语结构：

<pre data-overflow="wrap"><code><strong>请分析这个由三重引号分隔的文档和一个问题。读懂后仅通过文档的内容来回答问题，在回答问题时需要引用文档中的段落或结论。如果文档中没有回答此问题所需的信息，那么只需写上：“信息不足”。如果提供了问题的答案，必须用特殊格式注释它。请使用以下格式来引用相关段落Yinyong 。 
</strong>
"""&#x3C;在这里插入文档>"""

我的问题：&#x3C;插入问题>
</code></pre>

提示语示例：


```
请分析这个由三重引号分隔的文档和一个问题。读懂后仅通过文档的内容来回答问题，在回答问题时需要引用文档中的段落或结论。如果文档中没有回答此问题所需的信息，那么只需写上：“信息不足”。如果提供了问题的答案，必须用特殊格式注释它。请使用以下格式来引用相关段落Yinyong 。 

"""
什么是「小语 GPT」？
小语 GPT 所提供的内容生成功能所接入的服务提供商为微软的 Azure OpenAI 服务，支持用户轻松访问 GPT-3.5 和 GPT-4 模型。这些模型可以轻松适应特定的任务，包括但不限于内容生成、汇总、语义搜索和自然语言到代码的转换。
目前微软的 Azure OpenAI 服务仅面向企业客户提供，这是目前国内合法使用 OpenAI 服务的唯一途径。提示语科技（北京）有限公司目前已经获得微软授权。
"""
"""
比较小语 GPT、Azure OpenAI 和 OpenAI
相较于其它生成性模型，OpenAI 的 GPT 模型具有显著的潜在优势。然而，若不经过精心设计并采纳全面的缓解措施，这类模型可能产生错误甚至有害的内容。
Azure OpenAI 服务通过 OpenAI GPT-3.5、GPT-4 和 DALL-E 模型为企业客户提供高级语言 AI，更加关注实用安全性。借助Azure OpenAI，企业客户在运行与OpenAI 相同的模型时可获得 Microsoft Azure 的安全功能。 
在保留了 OpenAI 的 GPT 强大生成能力和 Azure OpenAI 服务安全功能的基础上，小语 GPT 针对国内政策对内容生成实施了更严格的规范，包括但不限于遵守法律法规、尊重社会公德、维护公序良俗，体现社会主义核心价值观、防止歧视性内容、避免不公平竞争、防止虚假信息传播，以及不侵犯他人肖像、隐私、知识产权等权益。
"""

我的问题：小语 GPT 是提示语科技自研的吗？
```


<figure><img src="/images/image-12.png" alt="" /><figcaption></figcaption></figure>

