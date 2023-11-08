---
Authors:
  - Rebecca L. Jackson
  - Timothy T. Rogers
  - Matthew A. Lambon Ralph
_links:
  - https://www.nature.com/articles/s41562-020-01034-z
tags:
  - semantic
  - multimodal
  - learning
---

# Main Ideas
This papers discuss a reverse engineering approach to find [[neurocomputational building block]] that support [[controlled semantic cognition]] by systematically varying the structure of computational model and assess the **functional consequences**.

This paper claims to found the best architectural properties that best promote two core functions of [[semantic system]].

> [!Core functions]
> - Abstraction
> Brain must have an ability to abstract the *context sensitive* information into *context invariant* concept that is useful to anticipate the future event.
> - Realization
> Moreover, brain must also have a capacity to bind some context invariant information to specific context of immediate task at hand.

## Goals
- Best neurocomputational machinery suitable for two core functions of **semantic cognition**
## Method
- Varying the computational building blocks of *spokes and hubs* model and evaluate the functional capacity
## Claims
The authors claims that above two functions are best achieved in models with a single, deep **multimodal hub** with **sparse connections** from **modality-specific regions**.

## Required Knowledges
### Reverse engineering
### Multimodal hub
### Sparse connection
### Modality specific region
### Quantification of functional performance
#### Abstraction
#### Realization

# Contents
## Core functions for semantic cognition
Research in semantic cognition largely focused on how *input* information (such as that from sensory, motor and linguistic) be represented with [[conceptual structure]]. This ability is thought to be arise from sensitivity to patterns of *covariation* in experience. That is conceptually information from one **semantic concept**.

> [!Covariation]
> Is this essentially relevant to **vector  encoding** of information?

For example, when we are talking about *birds*. They possess many common features such as beaks, feather, wings, flying ability and even the name *bird*. But birds do vary **wildly** in appearances.

So, in this view, **[concepts](semantic%20concept)** reflect [clusters](cluster) in the **high-order** covariance structure of experience.

> [!Against the flow]
> Is there such the case where concept should be in the low-order covariance structure?

However, such the idea is not suit to learning experience distributed across many [episodes](episode). Birds do not fly while lay eggs, but they, somehow, are bundled together as one whole concept. Each episodes provides a partial information about concepts while such a exposure may be highly context and modality specific. The example here is learning about bird physiology without dissecting it. So the [[abstraction]] here **must** extract covarying information from these contexts.

Moreover, when we talk about the second core functional requirements for semantic systems, it seems to be at odd with the first core function. The [[context sensitivity]] function of semantic cognition provides flexibility to generate task-relevant similarity structure. For instance, when considering the action upon piano and keyboard, they are highly similar but vastly different when consider similarity in their weights. This also permit the construction of ad hoc category *things that fit in a pocket*.

So, from above narrative, three core functional consequences are required for ideal semantic cognition system.
1. It must acquire representations that capture overall conceptual similarity structure - Apart from their input counterparts
2. It must acquire context independent conceptual representations from context-specific partial information from many episodes
3. It must adapt to context to generate context-sensitive behaviors

## Proposals about the neural architecture of semantic representation
There were some proposed structure but mostly without their mechanistic precision in implementation of context-specific and context-independent situations. This papers aim to **formally** compare and contrast the existing architectures. 

### Proposed hypotheses
#### Wernicke's proposal
Semantic processing reflects *direct, interactive communication among various associated surface representations*, - perceptual, motor, linguistic, affective and so on. This foreshadows modern [[embodied cognition]] views, that has been explored computationally.

#### Multiple multimodal hub
Important in mediating the interactions between sensorimotor modality. [Convergence zones](convergence%20zone) may connect different modalities within a network that adopts multiple hubs. Such hubs **could be** the sole vehicles for cross-modal communication. 
**OR**
They could connect via a broader multimodal region providing hierarchical convergence of information.

#### Single multimodal hub (This paper support)
This idea is supported by convergent of evidences:
- Computational (Timothy T. Roger previous work)
	- Rogers, T. T., Lambon Ralph, M. A., Garrard, P., Bozeat, S., McClelland, J. L., Hodges, J. R., & Patterson, K. (2004). _Structure and Deterioration of Semantic Memory: A Neuropsychological and Computational Investigation. Psychological Review, 111(1), 205–235._ doi:10.1037/0033-295x.111.1.205
	- Mahon, B. Z., & Caramazza, A. (2008). _A critical look at the embodied cognition hypothesis and a new proposal for grounding conceptual content. Journal of Physiology-Paris, 102(1-3), 59–70._ doi:10.1016/j.jphysparis.2008.03.004
- Neuropsychological
- Neuroimaging
	- Binney, R. J., Embleton, K. V., Jefferies, E., Parker, G. J. M. & Lambon Ralph, M. A. The ventral and inferolateral aspects of the anterior temporal lobe are crucial in semantic memory: evidence from a novel direct comparison of distortion-corrected fMRI, rTMS, and semantic dementia. Cereb. Cortex 20, 2728–2738 (2010).
	- 12. Visser, M., Jefferies, E., Embleton, K. V. & Lambon Ralph, M. A. Both the middle temporal gyrus and the ventral anterior temporal area are crucial for multimodal semantic processing: distortion-corrected fMRI evidence for a double gradient of information convergence in the temporal lobes. J. Cogn. Neurosci. 24, 1766–1778 (2012).
- Neurophysiological
- Neurostimulation

## Results

The models were fully recurrent neural networks with activity unfolding over time, train in the same environment **to the same performance**. Differing only in their **connectivity**.
- RNNs
- Same training
- Train to the same performance (How???)
- Differ only in connectivity

### Data
The data was created as activation pattern for 16 items in **three abstract modalities**. Designed to capture central challenge of conceptual abstraction. Mean that conceptual structure was latent but strongly different from apparent structure in any one of modalities.

![[Screenshot 2566-11-08 at 06.37.23.png]]
16 Concepts - 12 features
- **A** Covariation structure
	- Black/White pixels indicate the existences of covary signal
	- Red boxes indicate features that strongly **covary** across modals
	- Orange, Yellow, Green boxes indicate features with slightly strong, medium and loose **covariant** across modalities.
- **B \[Phase 1\]** Context independent similarity structure matrix across all modalities - 16 concept
	- This should indicate context-insensitivity similarity structure that should be recovered from [[abstraction]]
- **C \[Phase 2\]** Context-sensitive similarity structure that should be constructed from *realization* functionality - 144 input/output patterns
	- 144 from 16 concepts with 9 tasks (context)
	- Right - similarity based on *control signal*
	- Middle - from B
	- Left - similarity from context-independent signal and context signal
		- This should be in form of some convolution since the *context* is meant to filter/activate only a specific output

> [!Question]
> From distance structure, we can actually estimate the embedding dimension of these feature points using some assumption about the coverage of points/ density at higher dimension. Could it be generated from that?

![[noise_corr.png]]
The context signals correlation pattern is **imitation from noise/uniform distribution over space of features combination** (but with structural generation 🫠 in MATLAB used by authors exactly what I guessed) 
### Training Procedures
#### Initial phase
- Receive input from a single modality
- Optimize reproduce activation pattern in each modality
	- References
		- Farah, M. J. & McClelland, J. L. A computational model of semantic memory impairment: modality specificity and emergent category specificity. J. Exp. Psychol. Gen. 120, 339–357 (1991).
		- Rogers, T. T. et al. Structure and deterioration of semantic memory: a neuropsychological and computational investigation. Psychol. Rev. 111, 205–235 (2004).
		- McNorgan, C., Reid, J. & McRae, K. Integrating conceptual knowledge within and across representational modalities. Cognition 118, 211–233 (2011).
#### Second phase
- Control signal added as context for different tasks
- Reproduce activation in output units of item and task-relevant unit. (???)

#### Target
Correlation patterns between item-item pairs.

#### Optimization
Hidden layer's activation patterns are correlated with the true conceptual similarities. Conceptual similarity is also correlation matrix

> [!Important]
> The highest correlation between activation pattern and conceptual similarities indicate the most **suitable** models for semantic cognition

> [!Question]
> This seems to be based on linear representation? by utilizing correlation and such. Is linear correlation well-defined in nonlinear representation space?

### Evaluation
- Conceptual abstraction score $\to$ similarity to target correlation matrix
- Learning speed
- Multimodal structure (ignoring modality-specific structure) across context

![![Neuroscience/Neuroscience/Journal Club 2023/#^Table2]]
## Results
### Phase 1: Conceptual representation without control signal $\iff$ context 
Authors found differences in conceptual abstraction scores. 
#### Findings
##### Conceptual Score
$$\text{Spokes-Only} < \text{Bimodal Hubs} < \text{Shallow Multimodal Hub} \sim \text{Deep Multimodal Hub} > \text{Convergent Hubs}$$
1. Better with hub
2. Better with multimodal hub
3. Depth found no significant effect
4. Hierarchical convergence
5. Convergence hub had a significant detrimental effect 
	1. $\text{Deep Multimodal Hub} > \text{Convergent Hubs}$
	2. $\text{Multimodal Hub + Shortcut} > \text{Convergent Hubs + Shortcut}$
6. Shortcut helps
	1. In both multimodal hub and convergent hub
> [!Important]
> Multimodal Hub + Shortcut performed best.

![[Screenshot 2566-11-08 at 00.05.44.png]]

##### Learning
![[Screenshot 2566-11-08 at 00.03.42.png]]
- Shortcut alleviate the score while also speed up the learning
- Multimodal presence improve learning greatly
- Depth did not significantly improve anything

### Phase 2: Controlled semantic cognition
This addressed full challenge of controlled semantic cognition.
#### Findings
##### Conceptual abstraction score
![[Screenshot 2566-11-08 at 08.38.39.png]]

##### Learning
![[Screenshot 2566-11-08 at 08.42.10.png]]

##### Context sensitivity
In the experiment, locations of control signals induced as context affects the model differently.
![[Screenshot 2566-11-08 at 17.16.42.png]]

### Phase 3: Accounting for empirical phenomena with the reverse-engineered model
This section try to relate the proposed model with existing evidence
- \[Physical/Anatomical\] How does the structure accord with existing anatomical evidence of semantic network? 
	- From phase 1 and phase 2
		- Controlled semantic cognition is best achieved within architecture employing a single, deep, multimodal hub and shortcut connections.
	- Proposes
		- Sparse long-range shortcut, addition to region-to-region connection 
		  ```mermaid
		  graph LR;
		  A[Posterior modality-specific region] --> B[Multimodal hub]
		  ```
			- This has some evidences in white matter connection
			- Connectivity between anterior and posterior subsections of the [[fusiform gyrus]]
		- Semantic control should connect with semantic regions primarily via more posterior regions **distal** to the anterior temporal hub
			- No definitive evidence yet
			- Core [[ventral anterior temporal lobe]] hub **does** have few connections to distal regions (from references)
- \[Functional\] Does the model explain behavioral/neuronal phenomena?
	- Distinct neuropsychological syndromes
		- Semantic Aphasia characterized by loss ability to match the context to semantic concept
		- Semantic dementia represented by loss of representation in brain (loss of concept)
			- This only capture some of the expected result, but trends were observed in real phenotype![[Screenshot 2566-11-08 at 12.25.15.png]]
```mermaid
graph TD;
  A[Damage] --> B[anterior temporal hub]
  A --> C[temporoparietal control regions]
  B --> D[Semantic dementia SD]
  C --> E[Semantic aphasia SA]
  D --> F[Degraded representation]
  F --> G[Remove connections to/from \n multimodal hub]
  E --> H[Disordered control]
  H --> I[Adding noise to control unit]
```

- Functional brain imaging
	- Classical neuroimaging experiments
		- Participants viewed stimulus (word or picture) and retrieves color or its action
		- Identical stimulus have different functional activation when associated with different tasks
		- Result is <br>![[Screenshot 2566-11-08 at 12.04.52.png]]
		- Differences were found in only spokes and hidden layer 1
# Strong point
- Converging evidences
# Weak point
- Magnitude of statistical finding should not be addressed since it contains no meaning in $F$ score. This is not good to infer the intensity of diversity in resulting conceptual abstraction scores. Even Hedge's $g$ would not make this better. 
![[Screenshot 2566-11-07 at 20.png]]