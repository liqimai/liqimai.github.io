---
layout: post
title: "关于ICML-2019高引用图神经网络论文SGC"
excerpt: ""
modified: 31/12/2021, 01:52:24
tags: [GNN, SGC]
comments: true
category: blog
related_posts: false
timeinfo: false
---

##### The english version of this article is available at [http://liqimai.github.io/blog/SGC-english/](../SGC-english/)

### 摘要
本文想指出发表于ICML-2019的高引用图神经网络论文 “Simplifying Graph Convolutional Networks” 与我们ICLR-2019的投稿 “Label Efficient Semi-Supervised Learning via Graph Filtering” __高度相似__。

> 对方论文(简称SGC，发表于ICML-2019): <br/>
> Felix Wu, Tianyi Zhang, Amauri Holanda de Souza Jr., Christopher Fifty, Tao Yu, Kilian Q. Weinberger. “Simplifying Graph Convolutional Networks.” In <i>Proceedings of the 36th International Conference on Machine Learning</i>. 2019.
>
> 我方论文(简称GLP，曾投稿ICLR-2019): <br/>
> Qimai Li, Xiao-Ming Wu, Zhichao Guan. "Generalized Label Propagation Methods for Semi-Supervised Learning." (https://openreview.net/forum?id=SygjB3AcYX)  

我方论文后从ICLR撤稿，修改后以另一标题转投CVPR-2019，并最终获得发表: <br/>
> Qimai Li, Xiao-Ming Wu, Han Liu, Xiaotong Zhang, and Zhichao Guan. “Label Efficient Semi-Supervised Learning via Graph Filtering.” In <i>IEEE/CVF Conference on Computer Vision and Pattern Recognition</i>. 2019.

截止至2022年3月，对方论文已经被**引用近千次**[^3]，在图神经网络领域拥有很大的影响力。

在此我们想澄清以下事实：
1. **两篇论文高度相似，雷同之处包括方法、理论分析、实验、及图表。**
2. **我方论文比对方早公开四个多月。**

基于以上两点事实，我方在此声明：
1. 我方论文未曾抄袭SGC，希望大家不要误会。
2. 希望审稿人们勿要再要求我方后续工作引用SGC，因为我们已经正确引用了己方CVPR-2019的论文。
3. 希望诸位读者也能引用我方论文（即CVPR-2019最终版）。

### 1. 双方论文的相似之处

此处对比双方论文最早的公开版本，即对方在arXiv上的v1版本[^4]和我方ICLR-2019投稿版[^7]。双方相似之处包括方法、理论分析、实验、以及图表。

- 对方版本：[Simplifying Graph Convolutional Networks](https://arxiv.org/abs/1902.07153v1) (公开于2019年2月19日)
- 我方版本：[Generalized Label Propagation Methods for Semi-Supervised Learning](https://openreview.net/forum?id=SygjB3AcYX) (公开于2018年9月28日)

**具体雷同之处：**

<center>
<a href='/miscellaneous/SGC/compare-zh.pdf' target="_blank">点此放大对比表格</a>
<canvas id="the-canvas" style="width:100%;" src='/miscellaneous/SGC/compare-zh.pdf'></canvas>
</center>

### 2. 双方论文的时间顺序

我方论文最早公开于2018年9月28日，对方论文最早公开于2019年2月19日，公开时间比我方**晚四月有余**。ICML-2019论文投稿起始时间为2019年1月7日，亦晚于我方公开时间三月有余。具体时间线的详细说明如下：

- 对方论文共有两个公开版本。其最早的版本于2019年2月19日上传至arXiv[^4]。在论文被ICML-2019接收后，对方于同年6月20日在arXiv更新了其最终版[^5]。ICML官方网站上的版本[^6]公布时间不详，但应该是在2019年6月ICML会议结束之后。  

- 我方论文最早曾以“Feature Propagation for Semi-Supervised Learning”为标题于2018年2月投稿至ICML-2018，但此次为封闭审稿，并未公开。之后，我方论文的GLP版本于2018年9月28日投稿到ICLR-2019，在OpenReview平台进行公开审稿[^7]。最后，我方论文撤稿、再次修改后转投CVPR-2019并被接收[^8]。

| 日期 (YYYY/MM/DD)| 事件 |
|:---------------- |:------ |
| 2018/02/09 | 我方论文最初版提交至ICML-2018进行封闭审稿。 |
| 2018/09/28 | **我方论文提交至ICLR-2019，在OpenReview公开审稿**[^7]。|
| 2018/11/16 | 我方论文撤稿修改后提交至CVPR-2019。 |
| 2019/01    | 对方论文提交至ICML-2019[^9]。|
| 2019/01/28 | 我方论文(GLP版本)上传至arXiv。 |
| 2019/02/19 | **对方上传了最早的公开版本至arXiv**[^4]。|
| 2019/06/20 | 对方上传第二版至arXiv[^5]。ICML官方也在近期公开了对方论文的最终版本[^6]。|
| 2019/06/28 | 我方上传CVPR-2019最终版至arXiv[^8]。 |


### 3. 后续

1.对方论文在其最初的公开版本中[^4]**并未引用我方论文**。2019年3月在发现对方在arXiv的公开版本后，我方震惊于对方论文与我方论文的相似程度，**曾向ICML-2019程序主席发邮件反映，但并未收到任何回复**。在对方论文被ICML-2019接收后，我方曾发邮件跟对方论文作者沟通，希望对方能引用我们的工作，并对比两篇文章的区别，给予我方应有的credit。对方回复说他们的工作是独立做出，并同意引用我方论文。在2019年6月ICML会议结束之后，对方才在arXiv更新了论文第二版也是最终版[^6]并在相关工作部分(第四章)简要提及我方论文：“Li et al.(2019) propose a generalized version of label propagation and provide a similar spectral analysis of the renormalization trick.”

2.由于两篇论文从核心方法到技术细节都过于相似，对方的解释未能让我方信服。GLP是我们AAAI-2018论文[^10]的后续工作，比对方论文早近一年时间，最早曾投稿到ICML-2018。如果我方论文未被CVPR-2019接收，那在SGC被ICML-2019接收后，将几无可能发表。

3.由于对方论文在图神经网络领域有很大影响力(近千次引用)，**导致有些读者误以为我方抄袭对方论文**。曾有业内人士私下询问为何我方论文与对方论文如此相似，我们只能无奈解释我方论文比对方早公开几个月。并且，在我们后续工作投稿中，常有审稿人要求我们引用对方论文。可实际上，我们已经正确地引用了我方CVPR-2019的论文。


基于以上理由，我们觉得有必要公开澄清事实。

#### 参考文献
[^3]: 引用数据来自于 [Google Scholar](https://scholar.google.com.hk/scholar?q=simplifying+graph+convolutional+networks)。
[^4]: [SGC最早的公开版本](https://arxiv.org/abs/1902.07153v1)。
[^5]: [SGC被ICML-2019接收后arxiv上的最终版本](https://arxiv.org/abs/1902.07153v2)，与ICML官方公布版本相同。
[^6]: [ICML官方公布的SGC最终版本](http://proceedings.mlr.press/v97/wu19e/wu19e.pdf)。
[^7]: [我方最早公开版本](https://openreview.net/forum?id=SygjB3AcYX)。
[^8]: [我方CVPR的最终版本](https://openaccess.thecvf.com/content_CVPR_2019/papers/Li_Label_Efficient_Semi-Supervised_Learning_via_Graph_Filtering_CVPR_2019_paper.pdf)。
[^9]: ICML-2019 的论文提交开始于1月7日，结束于1月23日。详见 [call-for-paper](https://icml.cc/Conferences/2019/CallForPapers) 公告.
[^10]: Qimai Li, Zhichao Han, and Xiao-Ming Wu. "Deeper insights into graph convolutional networks for semi-supervised learning." Thirty-Second AAAI conference on artificial intelligence. 2018.
[^11]: Matthias Hein, and Markus Maier. "Manifold denoising as preprocessing for finding natural representations of data." AAAI. 2007.


<script>
    // console.log("Hello");
    supfix = document.querySelectorAll("sup[role='doc-noteref'] a.footnote[rel='footnote']");
    [...supfix].forEach(node => {
        // console.log(node.parentNode);        
        if (/^\d+$/.test(node.innerText)){
            node.innerText = "[" + node.innerText + "]";
        }
    });
</script>

<!-- <script src="https://mozilla.github.io/pdf.js/build/pdf.js"></script>   -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.6.347/pdf.min.js" integrity="sha512-Z8CqofpIcnJN80feS2uccz+pXWgZzeKxDsDNMD/dJ6997/LSRY+W4NmEt9acwR+Gt9OHN0kkI1CTianCwoqcjQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script id="script">
  // If absolute URL from the remote server is provided, configure the CORS
  // header on that server.
  var canvas = document.getElementById('the-canvas');
  var url = canvas.attributes['src'].textContent;
  // Loaded via <script> tag, create shortcut to access PDF.js exports.
  var pdfjsLib = window['pdfjs-dist/build/pdf'];
  // The workerSrc property shall be specified.
  // pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://mozilla.github.io/pdf.js/build/pdf.worker.js';
  // Asynchronous download of PDF
  var loadingTask = pdfjsLib.getDocument(url);
  loadingTask.promise.then(function(pdf) {
    console.log('PDF loaded');
    // Fetch the first page
    var pageNumber = 1;
    pdf.getPage(pageNumber).then(function(page) {
      console.log('Page loaded');
      var viewport = page.getViewport({scale: 4});
      // Prepare canvas using PDF page dimensions
      canvas.height = viewport.height;
      canvas.width = viewport.width;
      // Render PDF page into canvas context
      var renderContext = {
        canvasContext: canvas.getContext('2d'),
        viewport: viewport
      };
      var renderTask = page.render(renderContext);
      renderTask.promise.then(function () {
        console.log('Page rendered');
      });
    });
  }, function (reason) {
    // PDF loading error
    console.error(reason);
  });
</script>
