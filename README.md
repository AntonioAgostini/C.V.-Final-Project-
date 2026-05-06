**Abstract**: AI-generated image detectors are typically evaluated under idealized conditions, where images
are clean, uncompressed, and sourced directly from generative models. In practice, however, images
circulating on social media have almost always undergone some form of post-processing each of which introduces
a distinct degradation signature that can disrupt detector performance. This project proposes a
unified multi-task deep learning framework that simultaneously addresses two forensic questions: whether
an image is real or AI-generated, and which type of post-processing alteration has been applied to it. A
further analytical objective investigates whether AI-generated and real images respond differently to the
same post-processing operations, potentially revealing exploitable cross-class traces that can inform more
robust detection strategies.

**Dataset**: RRDataset: a real-world robustness benchmark containing real photographs and AI-generated images
with three splits: original, internet-transmitted, and re-digitized. Students may select a subset of the dataset,
comprehensive of all three classes, according to their available hardware.

**Task**: Given a single input image, a unified deep learning model must produce two predictions simultaneously: 
(1) a binary real/fake label indicating whether the image is a genuine photograph or AI-generated, and (2) a multi-class
transformation label indicating which post-processing alteration has been applied (original, internet-transmitted, or
re-digitalized). Both predictions are produced by a shared backbone, trained jointly with a combined loss function.
The project is structured in three phases: baseline unimodal training, joint multi-task training, and an analytical
phase investigating cross-class transformation traces.

**Main objectives**:
* Data preparation and subset selection: Download and preprocess the RRDataset, constructing a balanced
split across real/fake classes and transformation categories. Students should document their hardware-driven
subset choice and verify class balance before training.
* Multi-task unified model: Implement a shared backbone with two independent classification heads, one per
task. Train the model jointly using a weighted combination of the two cross-entropy losses, and experiment
with different loss weighting strategies. Evaluate both tasks simultaneously and compare against the unimodal
baselines to assess whether joint training improves, degrades, or leaves unchanged the performance of each
individual task.
* Performance analysis across transformation types: Break down real/fake detection accuracy separately for
each transformation category, original, transmitted, and each re-digitization method, to identify which postprocessing
operations are most damaging to detection performance and whether the pattern differs between
real and AI-generated images.
* Ablation study: Analyze how different weightings of the two task losses affect the trade-off between real/fake
accuracy and transformation classification accuracy, identifying whether the two tasks compete for representational
capacity or complement each other.

**References**:
* Li, Chunxiao, et al. ”Bridging the Gap Between Ideal and Real-world Evaluation: Benchmarking AI-Generated
Image Detection in Challenging Scenarios.” Proceedings of the IEEE/CVF International Conference on Computer
Vision. 2025. 
* Shao, Rui, Tianxing Wu, and Ziwei Liu. ”Detecting and grounding multi-modal media manipulation.” Proceedings
of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2023.
