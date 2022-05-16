<div align="center">
  
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/LogoPiML.png" alt="drawing" width="314.15926"/>

**A low-code interpretable machine learning toolbox in Python** 
</div>

[Examples](#Example) | [Installation](#Install) | [Usage](#Usage) | [Citations](#Cite)

PiML (or π·ML, /ˈpaɪ·ˈem·ˈel/) is a new Python toolbox for Interpretable Machine Learning model development and validation. Through low-code automation and high-code programming, PiML supports various machine learning models in the following two categories:

- **Inherently interpretable models**: 
1. EBM: Explainable Boosting Machine (Nori, et al. 2019; Lou, et al. 2013)
2. GAMI-Net: Generalized Additive Model with Structured Interactions (Yang, Zhang and Sudjianto, 2021)
3. ReLU-DNN: Deep ReLU Networks using Aletheia Unwrapper (Sudjianto, et al. 2020)

- **Arbitrary black-box models**，e.g.
1. LightGBM or XGBoost of varying depth
2. RandomForest of varying depth
3. Residual Deep Neural Networks

## Low-code Examples<a name="Example"></a>   
Click the ipynb links to run examples in Google Colab:  
1. BikeSharing data: <a style="text-laign: 'center'" target="_blank" href="https://colab.research.google.com/github/SelfExplainML/PiML-Toolbox/blob/main/examples/Example_BikeSharing.ipynb"><img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/LogoColab.png" width="20">  ipynb</a>  
2. CaliforniaHousing data: <a style="text-laign: 'center'" target="_blank" href="https://colab.research.google.com/github/SelfExplainML/PiML-Toolbox/blob/main/examples/Example_CaliforniaHousing.ipynb"><img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/LogoColab.png" width="20">  ipynb</a>  
3. TaiwanCredit data: <a style="text-laign: 'center'" target="_blank" href="https://colab.research.google.com/github/SelfExplainML/PiML-Toolbox/blob/main/examples/Example_TaiwanCredit.ipynb"><img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/LogoColab.png" width="20">  ipynb</a>   

Begin your own PiML journey with <a style="text-laign: 'center'" target="_blank" href="https://colab.research.google.com/github/SelfExplainML/PiML-Toolbox/blob/main/PiML%20Low-code%20Example%20Run.ipynb">this demo notebook</a>. 

## Installation<a name="Install"></a>  

```python
!pip install PiML  
```

## Low-code Usage on Google Colab<a name="Usage"></a>  

### Stage 1:  Initialize an experiment, Load and Prepare data

```python
from piml import Experiment
exp = Experiment(platform="colab")
```

```python
exp.data_loader()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/data_loader.png">

```python
exp.data_summary()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/data_summary.png">

```python
exp.data_prepare()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/data_prepare.png">

```python
exp.eda()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/data_eda.png">

### Stage 2:  Train intepretable models
```python
exp.model_train()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/model_train.png">


### Stage 3. Explain and Interpret
```python
exp.model_explain()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/model_explain.png">

```python
exp.model_interpret() 
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/model_interpret.png">

### Stage 4. Diagnose and Compare
```python
exp.model_diagnose()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/model_diagnose.png">

```python
exp.model_compare()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/model_compare.png">



## Arbitrary Black-Box Modeling
For example, train a complex LightGBM with depth 7 and register it to the experiment: 

```python
from lightgbm import LGBMRegressor
pipeline = exp.make_pipeline(LGBMRegressor(max_depth=7))
pipeline.fit() 
exp.register(pipeline=pipeline, name='LGBM')
```

Then, compare it to inherently interpretable models (e.g. EBM and GAMI-Net): 
```python
exp.model_compare()
```
<img src="https://github.com/SelfExplainML/PiML-Toolbox/blob/main/examples/results/model_compare2.png">



## Citations<a name="Cite"></a>  

<details open>
  <summary><strong>PiML, ReLU-DNN Aletheia and GAMI-Net</strong></summary><hr/>

  "PiML: A Python Toolbox for Interpretable Machine Learning Model Development and Validation" (A. Sudjianto, A. Zhang, Z. Yang, Y. Su, N. Zeng and V. Nair, 2022)  

  ```latex
  @article{sudjianto2022piml,
  title={PiML: A Python Toolbox for Interpretable Machine Learning Model Development and Validation},
  author={Sudjianto, Agus and Zhang, Aijun and Yang, Zebin and Su, Yu and Zeng, Ningzhou and Nair Vijay},
  journal={To appear},
  year={2022}
  }
  ```
  
  "Designing Inherently Interpretable Machine Learning Models" (A. Sudjianto and A. Zhang, 2021)  <a href="https://arxiv.org/abs/2111.01743">arXiv link</a>  
  
  ```latex
  @article{sudjianto2021designing,
  title={Designing Inherently Interpretable Machine Learning Models},
  author={Sudjianto, Agus and Zhang, Aijun},
  journal={arXiv preprint:2111.01743},
  year={2021}
  }
  ```

  "Unwrapping The Black Box of Deep ReLU Networks: Interpretability, Diagnostics, and Simplification" (A. Sudjianto, W. Knauth, R. Singh, Z. Yang and A. Zhang, 2020) <a href="https://arxiv.org/abs/2011.04041">arXiv link</a>  
  
  ```latex
  @article{sudjianto2020unwrapping,
  title={Unwrapping the black box of deep ReLU networks: interpretability, diagnostics, and simplification},
  author={Sudjianto, Agus and Knauth, William and Singh, Rahul and Yang, Zebin and Zhang, Aijun},
  journal={arXiv preprint:2011.04041},
  year={2020}
  }
  ```

  "GAMI-Net: An Explainable Neural Network based on Generalized Additive Models with Structured Interactions" (Z. Yang, A. Zhang, and A. Sudjianto, 2021) <a href="https://arxiv.org/abs/2003.07132">arXiv link</a>  

  ```latex
  @article{yang2021gami,
  title={GAMI-Net: An explainable neural network based on generalized additive models with structured interactions},
  author={Yang, Zebin and Zhang, Aijun and Sudjianto, Agus},
  journal={Pattern Recognition},
  volume={120},
  pages={108192},
  year={2021}
  }
  ```
</details>  


<details open>
  <summary><strong>EBM and GA2M</strong></summary><hr/>
  
  "InterpretML: A Unified Framework for Machine Learning Interpretability" (H. Nori, S. Jenkins, P. Koch, and R. Caruana, 2019)  
  
  ```latex
  @article{nori2019interpretml,
  title={InterpretML: A Unified Framework for Machine Learning Interpretability},
  author={Nori, Harsha and Jenkins, Samuel and Koch, Paul and Caruana, Rich},
  journal={arXiv preprint:1909.09223},
  year={2019}
  }
  ```

  "Accurate intelligible models with pairwise interactions" (Y. Lou, R. Caruana, J. Gehrke, and G. Hooker, 2013)   
  
  ```latex
  @inproceedings{lou2013accurate,
  title={Accurate intelligible models with pairwise interactions},
  author={Lou, Yin and Caruana, Rich and Gehrke, Johannes and Hooker, Giles},
  booktitle={Proceedings of the 19th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining},
  pages={623--631},
  year={2013},
  organization={ACM}
  }  
  ```
</details>


