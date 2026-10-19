# CLIP & LLaVA — Multimodal AI Laboratory

A practical laboratory exploring **multimodal artificial intelligence**, focusing on image-text alignment, zero-shot classification, semantic image retrieval, visual question answering, and multimodal assistants.

The project investigates two complementary vision-language architectures: **CLIP** and **LLaVA**.

## 1. Project Overview

The laboratory covers 13 exercises and a final mini-project, progressing from fundamental vision-language concepts to building a functional multimodal image assistant.

**Main objectives:**

- Understand contrastive and generative vision-language architectures.
- Perform zero-shot image classification using CLIP.
- Explore prompt engineering and image-text similarity.
- Build a semantic image retrieval system.
- Perform Visual Question Answering (VQA) using LLaVA.
- Investigate visual hallucinations.
- Integrate CLIP and LLaVA into a multimodal assistant.

## 2. Technologies

| Technology | Purpose |
|---|---|
| Python 3.11 | Programming language |
| Jupyter Notebook | Experiments and documentation |
| PyTorch | Deep learning framework |
| Hugging Face Transformers | CLIP implementation |
| CLIP ViT-B/32 | Classification and retrieval |
| LLaVA 1.5 7B (GGUF Q4) | Visual question answering |
| llama-cpp-python | Quantized LLaVA inference |
| Pillow | Image processing |
| NumPy / Pandas | Data processing and evaluation |

The experiments were executed in a **CPU-only environment**.

## 3. Laboratory Experiments

### CLIP Experiments

- Image and text embedding generation.
- Zero-shot image classification.
- Prompt engineering and similarity analysis.
- Image database creation using 512-dimensional embeddings.
- Text-to-image retrieval using cosine similarity.

### LLaVA Experiments

- Vision-language architecture exploration.
- Image descriptions and natural-language question answering.
- VQA evaluation using five images and 25 questions.
- Visual hallucination analysis.
- Comparison between contrastive and generative multimodal models.

## 4. Experimental Results

| Experiment | Result |
|---|---|
| CLIP cat/dog classification | 100% accuracy (10/10) |
| CLIP dog recognition | 99.05% probability among three candidate descriptions |
| CLIP image database | 20 images, 512-dimensional embeddings |
| CLIP retrieval | Top-5 cosine similarity ranking |
| LLaVA VQA evaluation | 72% accuracy (18/25) |
| Hallucination experiment | Invented a location for a nonexistent bicycle |

These results were obtained on small experimental datasets and should not be interpreted as general benchmark performance.

## 5. Final Mini-Project — Multimodal Image Assistant

The final mini-project integrates CLIP and LLaVA into a single notebook-based assistant supporting two modes.

### Mode A — Image Question Answering

The user provides an image and a natural-language question.

**Workflow:**

`Image + Question → LLaVA → Generated Answer`

### Mode B — Image Retrieval + Question Answering

The user provides a text query. CLIP retrieves the five most relevant images, and LLaVA answers questions about a selected image.

**Workflow:**

`Text Query → CLIP → Top-5 Images → Selected Image + Question → LLaVA → Generated Answer`

This demonstrates how contrastive retrieval and generative visual understanding can be combined within one application.

## 6. Installation

Create a Python virtual environment and install the required dependencies:

```bash
python -m venv .venv
source .venv/bin/activate

pip install torch transformers huggingface_hub \
    llama-cpp-python gguf pillow numpy pandas \
    jupyterlab ipykernel
```

On Windows, activate the environment using `.venv\Scripts\activate`.

The installation of `llama-cpp-python` may require additional build tools depending on the operating system.

## 7. Models

### CLIP

The following model is downloaded through Hugging Face Transformers:

`openai/clip-vit-base-patch32`

### LLaVA

The project uses a quantized LLaVA 1.5 7B model.

**Language model:**

- Repository: `mys/ggml_llava-v1.5-7b`
- File: `ggml-model-q4_k.gguf`

**Vision projector:**

- Repository: `second-state/Llava-v1.5-7B-GGUF`
- File: `llava-v1.5-7b-mmproj-model-f16.gguf`

The projector was selected for compatibility with the multimodal loader in `llama-cpp-python 0.3.36`.

Model weights are not included in this repository due to their size. They are downloaded separately through Hugging Face.

## 8. Running the Laboratory

1. Clone or download this repository.
2. Install the dependencies.
3. Launch JupyterLab with `jupyter lab`.
4. Open the laboratory `.ipynb` notebook.
5. Ensure the required image files are available.
6. Execute the notebook cells in order.
7. Run the final mini-project demonstrations.

The mini-project uses Python functions within Jupyter Notebook and does not require a separate web server.

## 9. Limitations

The main limitations observed include:

- Small image database with limited visual diversity.
- Sensitivity of CLIP similarity scores to prompt wording.
- Visual hallucinations in LLaVA-generated answers.
- CPU inference latency for the 7B parameter model.
- Possible errors in counting, object recognition, and scene interpretation.

## 10. Conclusion

This laboratory demonstrates the complementary capabilities of **CLIP** and **LLaVA**.

CLIP provides efficient image-text matching and semantic retrieval, while LLaVA enables open-ended visual understanding and natural-language generation.

Combining the two models provides a practical foundation for more advanced multimodal assistants.

---

**Project type:** Academic laboratory — Multimodal AI

**Implementation:** Python / Jupyter Notebook

**Models:** CLIP ViT-B/32 and LLaVA 1.5 7B
