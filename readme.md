# MAFI: A Multi-Modal Attention Framework Integrating Molecular Subgraphs and Homologous Sequence Features for Drug-Target Affinity Prediction


 MAFI: A Multi-Modal Attention Framework that combines protein homology sequence generation with multi-scale protein graph construction to enhance Drug-Target Affinity prediction. It uses the ESM3 model for creating homology sequences, enriching protein sequence diversity perception and improving generalization. The multi-step protein subgraph mapping captures structural info at different scales. Along with BILSTM and attention mechanisms, MAFI offers high interpretability, making it a credible tool for drug discovery.


## 💡 MAFI-DTA Framework
![Model overview diagram1]
The key components of the MAFI model are as follows:

(1) Homologous Sequence Enhancement  
Using the ESM3 model to generate homologous sequences of proteins and fuse them into enhanced feature vectors. This enriches the model's perception of protein sequence variability, enhances its generalisation ability for different protein structures, and aids in accurately identifying key amino acid residues and their interaction patterns.  

(2) BILSTM and Attention Mechanism  
Processing sequence data to capture long-range dependencies. BILSTM captures contextual information, while the attention mechanism highlights important sequence regions, enhancing the model's understanding of sequence data and its interpretability in practical applications.

(3) Cross-Modal Graph Attention Mechanism  
Fuses molecular graph and protein subgraph features, using a multi-head attention mechanism to dynamically allocate feature weights from multiple perspectives, focusing on key features to achieve effective integration of cross-modal features.

(4) Graph Neural Network
Both the molecular graph and protein subgraph neural networks utilise graph neural networks to extract structural features. The molecular graph neural network uses GINConv layers and batch normalisation layers to extract molecular topological features, and employs global pooling to aggregate node features into graph-level features. Protein subgraph neural networks construct protein subgraph mappings with different strides to extract local and global features of proteins. Together, they provide the model with a deep understanding of drug and target structures.

These modules collaborate to enable the model to accurately predict drug-target affinity.
 
## 🧠 File list
vocabulary_builder.py: Used to build a vocabulary, containing the TorchVocab, Vocab, and WordVocab classes, as well as the main function to generate and save the vocabulary.

utils.py: Provides a set of utility functions, including model training, prediction, and performance metric calculation.

molecular_interaction.py: Defines the MolecularInteractionDataset class for processing molecular and protein interaction datasets.

main.py: The main program file, containing the workflow for data preprocessing, model training, and evaluation.

interaction_network.py: Defines the model architecture, including the SpatialFeatureAggregator, HeterogeneousAttentionLayer, MolecularGraphNetwork, and CrossModalInteractionNet classes.

graphmaker.py: Provides functions for constructing molecular and protein contact graphs.

generate_homologous.py: Contains functions for generating homologous protein sequences and related utility functions.

These files collectively form a multi-modal attention framework for drug-target affinity prediction.


## 📁 Dataset
To ensure the accuracy of the model, we utilized six datasets: Davis, KIBA, PDBbind, Toxcast, Binding DB, and Metz. ‘Davis_processed.csv’ records protein-drug molecule binding affinity data, which is used for model training and validation. ‘KIBA_processed.csv’ integrates multi-source data and records ligand-receptor protein binding constants. ‘PDBbind_processed.csv’ provides three-dimensional structures and binding affinity data for protein-ligand complexes. ‘Toxcast_processed.csv’ covers toxicological data for various chemicals. ‘BindingDD_processed.csv’ contains binding data for protein-ligand complexes. ‘Metz_processed.csv’ is used for toxicity prediction studies of compounds.
Multiple datasets fully demonstrate the model's generalization capability.


Before commencing model training, we employed the ESM3 model to predict contact maps. The ESM3 model can predict the spatial proximity relationships between atoms in protein-ligand complexes based on protein sequence information, thereby generating corresponding contact maps. These contact maps include important details such as contact locations, contact types, and contact strengths, providing the model training with rich structural feature data and aiding the model in better understanding the interaction patterns between proteins and ligands.
The generated protein-ligand complex contact maps should be properly stored in a folder named ‘{dataset_name}_npy_contact_maps’ to enable quick and accurate access and reading during model training, ensuring the efficiency and consistency of the entire model training process and laying a solid foundation for improving model performance.


## 🖥️ Requirements
You'll need to run the following commands in order to run the codes
```
conda env create -f requirements.yml
```
it will download all the required libraries
```
conda activate mafi
```
The code file can now be run.

## 🛠️ Run Code
```
python main.py 
```

## 🤖 Citation


