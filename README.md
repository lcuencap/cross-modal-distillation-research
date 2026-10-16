# Cross-Modal Knowledge Distillation: Research and Reproducibility Review

Research work carried out by Laura Cuenca during a university departmental collaboration. The goal was to understand how knowledge distillation can transfer information between modalities in computer vision and to assess how readily selected open-source research implementations could be reproduced.

This was an **informal exploratory report prepared for the director of the university's Computer Vision research line**. Its purpose was to give the group an initial overview of cross-modal knowledge distillation and help identify how these techniques might be relevant to several of the research projects they were already working on. It was intended as a starting point for discussion and technical exploration, not as a formal research paper or benchmark study.

**My contribution:** literature review, comparison of techniques, cloning repositories, and attempts to configure and run them. I did **not** implement the models, train new models, or produce benchmark results. The repositories reviewed belong to their original authors; their code is not included here.

## Questions explored

- What can a teacher model transfer to a student: final responses, intermediate features, or relationships between examples?
- What changes when teacher and student use different modalities, such as vision, audio, text, or sketches?
- Which practical details are needed to reproduce a research implementation: data, checkpoints, dependency versions, configuration files, and scripts?
- Which of these approaches could be potentially useful across the Computer Vision research line's existing projects?

## Reproducibility notes

| Project reviewed | Outcome during this study |
| --- | --- |
| [Acoustic Images Distillation](https://github.com/afperezm/acoustic-images-distillation) | Repository cloned; environment and input requirements were insufficiently documented for a reliable test. |
| [Xmodal-ViT](https://github.com/abhrac/xmodal-vit) | Repository cloned; setup and input requirements remained unclear. |
| [Speech2Video](https://github.com/michaelzhang-ai/Speech2Video) | The referenced repository could not be found at the time of the study. |
| [Text2Video](https://github.com/michaelzhang-ai/Text2Video) | Missing files or scripts prevented a complete test. |
| [MTDVocaLiST](https://github.com/xjchengit/mtdvocalist) | Missing files or scripts prevented a complete test. |

Across the attempts, dependency compatibility and incomplete setup instructions were recurring obstacles. This was a **reproducibility review**, not a comparison of model accuracy or speed.

## Technical synthesis

In cross-modal distillation, a teacher trained with one source of information guides a student that may use another. That creates design questions beyond ordinary model compression: how representations are aligned, whether paired data is available, how time is synchronized for video or audio, and whether the student can keep the useful signal when its input is less informative.

```mermaid
flowchart LR
    A[Teacher modality] --> B[Teacher representation]
    C[Student modality] --> D[Student representation]
    B --> E[Distillation objective]
    D --> E
    E --> F[Student training signal]
```

The review also considered possible applications in visual recognition and robotics, with the broader goal of identifying directions that could be useful for the research line's existing work. These are research directions discussed in the report, not implemented applications in this repository.

## What this work taught me

Research code is only useful to a new team when the execution path is explicit: compatible versions, available data and checkpoints, documented inputs, and an end-to-end example. The setup attempts made those requirements concrete and helped me distinguish an interesting paper from a result that I could independently verify.

## Academic report

The [original research report](report.pdf) is included as background reading. It was an informal internal exploration intended to support discussion within the Computer Vision research line. It contains illustrative methods and a university email address; it does not document trained models, original implementations, or verified benchmark results. The third-party repositories discussed are linked above rather than copied here.
