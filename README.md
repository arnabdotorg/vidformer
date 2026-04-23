# vidformer

[![Test](https://github.com/arnabdotorg/vidformer/actions/workflows/test.yml/badge.svg)](https://github.com/arnabdotorg/vidformer/actions/workflows/test.yml)
[![PyPI version](https://img.shields.io/pypi/v/vidformer.svg)](https://pypi.org/project/vidformer/)
[![Crates.io Version](https://img.shields.io/crates/v/vidformer)](https://crates.io/crates/vidformer)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/arnabdotorg/vidformer/blob/main/misc/Colab_Vidformer.ipynb)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](./LICENSE)

Vidformer is an open-source research software project for accelerating video and data visualization workflows.
See the [preprint on arXiv](https://arxiv.org/abs/2601.17221) for details.

Developed by the OSU Interactive Data Systems Lab.

![Vidformer teaser](misc/landing-page/static/images/teaser.png)

## Quick Start

To quickly try out Vidformer you can:

- [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/arnabdotorg/vidformer/blob/main/misc/Colab_Vidformer.ipynb)
- try the online [Vidformer Playground](https://ixlab.github.io/vidformer/playground/)

Or, you can deploy it yourself:

```bash
git clone https://github.com/arnabdotorg/vidformer
cd vidformer
docker build -t igni -f Dockerfile .
docker-compose -f vidformer-igni/docker-compose-local.yaml up
```

You can find details on this in our [Getting Started Guide](https://ixlab.github.io/vidformer/docs/getting-started.html).

## Why vidformer

Vidformer efficiently transforms videos, enabling faster annotation, editing, and processing of video data—without having to focus on performance. Just swap `import cv2` with `import vidformer.cv2 as cv2` to see video outputs instantly.

Vidformer uses a declarative specification format to represent transformations. This enables:

- **Transparent Optimization:** Vidformer optimizes the execution of declarative specifications just like a relational database optimizes relational queries.
- **Lazy/Deferred Rendering:** Video results can be retrieved on-demand, allowing for practically instantaneous playback of video results.

Vidformer usually renders videos 2-3x faster than cv2, and hundreds of times faster (*practically instantly*) when serving videos on-demand.

Vidformer builds on open technologies you may already use:

- **OpenCV:** A `cv2`-compatible interface ensures both you (and LLMs) can use existing knowledge and code.
- **Supervision:** [Supervision](https://supervision.roboflow.com/latest/)-compatible annotators make visualizing computer vision models trivial.
- **FFmpeg:** Built on the same libraries, codecs, and formats that run the world.
- **Jupyter:** View transformed videos instantly right in your notebook.
- **HTTP Live Streaming (HLS):** Serve transformed videos over a network directly into any media player.
- **Apache OpenDAL:** Access source videos no matter where they are stored.

## Installation

Vidformer is published in multiple forms depending on how you want to use it:

- **Python package:** `pip install vidformer`
- **Rust workspace:** `cargo build`
- **Server deployment:** `docker build -t igni -f Dockerfile .`

For full setup instructions, dependency details, and platform-specific notes, see:

- [Install guide](https://ixlab.github.io/vidformer/docs/install.html)
- [Getting started](https://ixlab.github.io/vidformer/docs/getting-started.html)
- [`vidformer` Rust crate README](./vidformer/README.md)
- [`vidformer-py` README](./vidformer-py/README.md)
- [`vidformer-igni` README](./vidformer-igni/README.md)

## Basic usage

A minimal Python workflow looks like this:

```python
import vidformer.cv2 as cv2

cap = cv2.VideoCapture("tos_720p.mp4")
ok, frame = cap.read()
```

Additional examples are available in:

- [Colab notebook](./misc/Colab_Vidformer.ipynb)
- [Docs site](https://ixlab.github.io/vidformer/docs/)
- [Playground](https://ixlab.github.io/vidformer/playground/)

## Documentation

- [🌐 Website](https://ixlab.github.io/vidformer/)
- [🌐 Docs](https://ixlab.github.io/vidformer/docs/)
- [🚀 Getting Started](https://ixlab.github.io/vidformer/docs/getting-started.html)
- [🐍 vidformer-py](https://ixlab.github.io/vidformer/vidformer-py/)
- [🛠️ vidformer core](https://ixlab.github.io/vidformer/vidformer/)

## Related assets and provenance

Vidformer does not publish model weights or training datasets in this repository. Instead, the repository includes code, examples, and deployment tooling for working with external media and model outputs.

- Sample media used in tests and examples is fetched from `https://f.dominik.win/data/dve2/`, including `tos_720p.mp4` and `apollo.jpg`.
- The playground and notebook demos also reference hosted sample media and derived artifacts under `https://f.dominik.win/vf-sample-media/`.
- Core source-code dependencies include FFmpeg, OpenCV, Apache OpenDAL, and Supervision; package-level dependency manifests are tracked in `Cargo.toml` and `vidformer-py/pyproject.toml`.
- The primary software and paper citation metadata is tracked in [`CITATION.cff`](./CITATION.cff).

## Repository governance

To support FAIR and reproducible software practices, this repository includes the following project-health documents:

- [Contributing guidelines](./CONTRIBUTING.md)
- [Code of conduct](./CODE_OF_CONDUCT.md)
- [Citation metadata](./CITATION.cff)
- [License](./LICENSE)

## About the project

**Cite:**

```bibtex
@misc{winecki2026_vidformer,
      title={Vidformer: Drop-in Declarative Optimization for Rendering Video-Native Query Results},
      author={Dominik Winecki and Arnab Nandi},
      year={2026},
      eprint={2601.17221},
      archivePrefix={arXiv},
      primaryClass={cs.DB},
      url={https://arxiv.org/abs/2601.17221},
}
```

**File Layout**:

- [*./vidformer*](./vidformer/): The core rendering library (Rust)
- [*./vidformer-py*](./vidformer-py/): The Python frontend
- [*./vidformer-igni*](./vidformer-igni/): The vidformer server
- [*./docs*](./docs/): The [project docs](https://ixlab.github.io/vidformer/docs/)

Vidformer components are detailed [here](https://ixlab.github.io/vidformer/docs/modules.html).

**License:** Vidformer is open source under [Apache-2.0](./LICENSE).
Contributions are welcome.

**Acknowledgements:** Vidformer is based upon work supported by the National Science Foundation under Awards #2118240 and #1910356.
