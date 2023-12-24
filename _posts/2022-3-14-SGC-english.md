---
layout: post
title: "About the Highly-Cited ICML-2019 GNN Paper SGC"
excerpt: ""
modified: 31/12/2021, 01:52:24
tags: [GNN, SGC]
comments: true
category: blog
related_posts: false
timeinfo: false
---

##### 本文的中文版本：[http://liqimai.github.io/blog/SGC-chinese/](../SGC-chinese/)

### Abstract

We want to point out that the highly-cited ICML-2019 GNN (graph neural network) paper “<i>Simplifying Graph Convolutional Networks</i>”, is **highly similar** to our ICLR-2019 submission “<i>Generalized Label Propagation Methods for Semi-Supervised Learning</i>”.

> The GNN paper (referred to as SGC, published in ICML-2019): <br/>
> Felix Wu, Tianyi Zhang, Amauri Holanda de Souza Jr., Christopher Fifty, Tao Yu, Kilian Q. Weinberger. “Simplifying Graph Convolutional Networks.” In <i>Proceedings of the 36th International Conference on Machine Learning</i>. 2019.
>
> Our paper (referred to as GLP, was submitted to ICLR-2019): <br/>
> Qimai Li, Xiao-Ming Wu, Zhichao Guan. “Generalized Label Propagation Methods for Semi-Supervised Learning.” (https://openreview.net/forum?id=SygjB3AcYX)

We withdrew our paper from ICLR-2019 during the rebuttal period and revised and resubmitted it to CVPR-2019 with another title, which was accepted and published.
> Qimai Li, Xiao-Ming Wu, Han Liu, Xiaotong Zhang, and Zhichao Guan. “Label Efficient Semi-Supervised Learning via Graph Filtering.” In <i>IEEE/CVF Conference on Computer Vision and Pattern Recognition</i>. 2019.
 
As of now (March 2022), the SGC paper has been <b>cited about 1000 times</b>[^3] and is a quite influential GNN paper.

Here, we want to clarify the following facts:
1. **The two papers are highly similar in method, theoretical analysis, experiments, and figures.**
2. **Our paper was made public more than four months earlier than SGC.**

Based on the above facts, here we want to state that:
1. We did not plagiarize the SGC paper. Hope people are aware of this.
2. We hope the reviewers of our follow-up works won't request us to cite the SGC paper again, because we'd already properly cited our CVPR-2019 paper. 
3. We hope others could also cite our CVPR-2019 final version.

### 1. Similarities between the two papers

Here, we compare the earliest public version of the two papers, i.e., the first version of SGC[^4] on arXiv and our submission to ICLR-2019[^7].

- The SGC paper (made public on 19th February 2019): [Simplifying Graph Convolutional Networks](https://arxiv.org/abs/1902.07153v1)  
- Our GLP submission (made public on 28th September 2018) : [Generalized Label Propagation Methods for Semi-Supervised Learning](https://openreview.net/forum?id=SygjB3AcYX) 


__Similarities:__

<center>
<a href='/miscellaneous/SGC/compare-en.pdf' target="_blank">Click here to zoom in</a>
<canvas id="the-canvas" style="width:100%;" src='/miscellaneous/SGC/compare-en.pdf'></canvas>
</center>



### 2. Timeline
Our GLP paper was made public on 28th September 2018, and the SGC paper was made public on 19th February 2019, <b>more than four months later than ours</b>. The submission of ICML-2019 started on 7th January 2019, more than three months later than our GLP paper. 

Timeline:

- There are two public versions of SGC. The first version was uploaded to arXiv on 19th February 2019[^4], and the second and final version was updated on 20th June 2019 after the ICML-2019 conference[^5]. The same version was also released on the PMLR website around the time.

- The earliest version of our paper was submitted to ICML-2018 in February 2018 titled as “Feature Propagation for Semi-Supervised Learning" for private review. We submitted the GLP version to ICLR-2019 for open review on 28th September 2018 [^7]. Finally, we withdrew it from ICLR-2019 and resubmitted a revised version to CVPR-2019, which was accepted. 

| Date (YYYY/MM/DD)| Events |
|:---------------- |:------ |
| 2018/02/09 | The first version of our paper was submitted to ICML-2018 for private review. |
| 2018/09/28 |__The GLP version of our paper was submitted to ICLR-2019 for open review__.[^7]|
| 2018/11/16 | A revised version of our paper was submitted to CVPR-2019. |
| 2019/01    | The SGC paper was submitted to ICML-2019.[^9]|
| 2019/01/28 | We upload the GLP version of our paper to arXiv. |
| 2019/02/19 | __The first version of SGC was uploaded to arXiv.__[^4]|
| 2019/06/20 | The second version of SGC was uploaded to arXiv[^5], which was also appeared on the PMLR website around the time.[^6]|
| 2019/06/28 | We uploaded the final version of our paper to arXiv[^8]. |


### 3. Follow-up


1. The first public version of SGC[^4] __did not cite our paper__. When we saw the first version of SGC on arXiv in March 2019, we were shocked by its high similarity with our GLP. __We tried to inform the program chairs of ICML-2019 about this matter by email but received no reply__. After SGC was accepted by ICML-2019, we contacted the authors by email and hoped them could cite our paper, compare the differences between their work and ours, and give proper credit to us. They replied that their work was done independently and promised to cite our paper in the final version. After the end of ICML-2019 conference, they uploaded the final version to arXiv, where they briefly mentioned our paper in related work (section 4) that “Li et al.(2019) propose a generalized version of label propagation and provide a similar spectral analysis of the renormalization trick.” 


2. Since the two papers are too similar in both core idea and technical detail, we are not convinced by their claim. GLP is the follow-up work of our AAAI-2018 paper[^10], which is almost one year earlier than SGC and was first submitted to ICML-2018. Had our work not been accepted by CVPR-2019, it may never get published after SGC was accepted by ICML-2019.


3. Since the SGC paper is quite influential in the GNN field (cited nearly 1000 times), __some people thought we plagiarized SGC__. We were once asked by an expert why our CVPR-2019 paper is so similar to SGC, and we had to explain that our paper was made public several months before SGC. We were also requested by some reviewers of our follow-up works to cite the SGC paper, even though we'd already properly cited our CVPR-2019 paper.

Based on the above reasons, we feel the need to clarify the facts.

#### Reference
[^3]: The citation data is from [Google Scholar](https://scholar.google.com.hk/scholar?q=simplifying+graph+convolutional+networks).
[^4]: [The earliest public version of SGC](https://arxiv.org/abs/1902.07153v1).
[^5]: [The final version of SGC on arXiv](https://arxiv.org/abs/1902.07153v2).
[^6]: [The final version of SGC on PMLR website](http://proceedings.mlr.press/v97/wu19e/wu19e.pdf).
[^7]: [The first public version of our GLP paper](https://openreview.net/forum?id=SygjB3AcYX).
[^8]: [The final version of our paper published in CVPR-2019](https://openaccess.thecvf.com/content_CVPR_2019/papers/Li_Label_Efficient_Semi-Supervised_Learning_via_Graph_Filtering_CVPR_2019_paper.pdf).
[^9]: Submissions of ICML-2019 opened on Jan. 7 and closed on Jan 23. See the [call-for-paper announcement](https://icml.cc/Conferences/2019/CallForPapers) of ICML-2019.
[^10]: Qimai Li, Zhichao Han, and Xiao-Ming Wu. "Deeper insights into graph convolutional networks for semi-supervised learning." Thirty-Second AAAI conference on artificial intelligence. 2018.
[^11]: Matthias Hein, and Markus Maier. "Manifold denoising as preprocessing for finding natural representations of data." AAAI. 2007.



<script defer>
    // console.log("Hello");
    supfix = document.querySelectorAll("sup[role='doc-noteref'] a.footnote[rel='footnote']");
    [...supfix].forEach(node => {
        // console.log(node.parentNode);        
        if (/^\d+$/.test(node.innerText)){
            node.innerText = "[" + node.innerText + "]";
        }
    });
</script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.6.347/pdf.min.js" integrity="sha512-Z8CqofpIcnJN80feS2uccz+pXWgZzeKxDsDNMD/dJ6997/LSRY+W4NmEt9acwR+Gt9OHN0kkI1CTianCwoqcjQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script defer>
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
