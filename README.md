# FRAIL: Few-shot Radar Anti-jamming via Imitation Learning with Feature Retrieval

> **Repository status:** Reserved repository for the manuscript currently under peer review.  
> The complete source code, simulation configurations, and dataset will be released after the paper is accepted and officially published.

## Overview

FRAIL is a few-shot radar anti-jamming framework based on imitation learning with feature retrieval. The method is designed for radar–jammer interaction scenarios in which only a small number of observations are available for previously unseen jamming conditions.

Instead of explicitly classifying the received jamming waveform into a predefined category, FRAIL directly uses the received I/Q waveform as the radar observation and retrieves task-relevant historical state–action experiences from an offline radar–jammer interaction dataset. The retrieved experiences are then used to guide anti-jamming policy adaptation under limited online samples.

The overall processing chain is:

```text
Jamming observation
    -> State–action feature embedding
    -> Historical behavior retrieval
    -> Anti-jamming policy optimization
    -> Radar waveform/action generation
    -> Radar–jammer interaction
    -> Reward feedback
```

## Main Components

The current manuscript contains three main components:

1. **State–action embedding**  
   A variational autoencoder (VAE)-based representation model is trained on historical radar–jammer interaction data to construct a compact embedding space for state–action pairs.

2. **Similarity-based behavior retrieval**  
   Under a few-shot unknown jamming condition, target observations are used to retrieve relevant historical interaction samples from the offline dataset according to their embedding similarity.

3. **Retrieval-guided policy adaptation**  
   Retrieved historical samples and newly collected online interaction samples are jointly used for policy optimization, allowing the radar to adapt its anti-jamming behavior with limited target-domain data.

## Radar–Jammer Simulation

The current simulation considers a multifunction radar and a self-protection jammer.

### Radar waveforms / actions

The radar can adapt its transmission strategy using waveform-level actions, including:

- LFM waveform configuration;
- carrier-frequency adaptation;
- pulse-parameter adjustment;
- decoy-pulse transmission.

### Jamming waveforms

The current study considers four representative jamming types:

- Spot jamming (SJ);
- Comb-spectrum jamming (CJ);
- Smeared spectrum jamming (SMSP);
- Intermittent sampling repeater jamming (ISRJ).

The waveform parameters of these jamming types are configurable and are used to construct both cross-type and unseen-parameter few-shot evaluation settings.

## Planned Repository Structure

```text
FRAIL/
├── README.md
├── requirements.txt
├── .gitignore
├── configs/
│   └── README.md
├── data/
│   └── README.md
├── src/
│   └── README.md
├── scripts/
│   └── README.md
└── results/
    └── README.md
```

After publication, the repository is planned to include:

- source code for FRAIL;
- radar and jammer waveform-generation scripts;
- simulation configuration files;
- training and testing hyperparameters;
- representative and/or complete radar–jammer interaction datasets;
- scripts for reproducing the main experiments and figures reported in the paper.

## Reproducibility

The manuscript is currently under peer review. To avoid releasing an incomplete implementation before the paper is finalized, the full code and dataset are not yet publicly available.

After acceptance and official publication, the complete reproducibility package will be released in this repository, including the source code, simulation configurations, and corresponding dataset used in the final version of the paper.

## Experimental Results Reported in the Manuscript

The current manuscript reports evaluation of:

- waveform reconstruction quality of the VAE embedding model;
- latent-space separability of jamming waveforms;
- few-shot anti-jamming performance under 50 / 100 / 150 online samples;
- comparison with DEN, PNN, and PathNet;
- catastrophic forgetting performance;
- robustness under additive white Gaussian noise;
- ablation of the embedding model and retrieval threshold;
- additional generalization tests under unseen waveform-parameter ranges.

> Numerical results, trained checkpoints, and reproduction scripts will be added after publication.

## Citation

If you use this work, please cite the final published version of the paper. Citation information will be updated after publication.

```bibtex
@article{frail2026,
  title   = {FRAIL: Few-shot Radar Anti-jamming via Imitation Learning with Feature Retrieval},
  author  = {Feng Xie and Huanyu Liu and Suxian Shi and Peiru Tian and Junbao Li},
  journal = {To appear},
  year    = {2026}
}
```

## Availability

A reserved GitHub repository is provided during peer review. The complete source code, simulation configurations, and corresponding dataset will be publicly released through this repository after the paper is accepted and officially published.

## Contact

For questions regarding the manuscript or future code release, please contact the corresponding author listed in the paper.
