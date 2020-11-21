# Gini-PCA
A. Charpentier, S. Mussard & T. Ouraga (2020)
***

### Gini PCA is a robust L1-norm PCA based on the generalized Gini index

In this package, we find:

  * Absolute contributions of the observations (cos²)
  * Relative contributions of the observations
  * Feature importance of each variable (U-statistics test)
  * Feature importance of each variable in the standard PCA (U-statistics test)
  * Grid search for detecting and minimizing the influence of outliers 
  * Outlier detection using Hotelling T2 
  * Example on Iris data below


### Install outlier_utils and iteration-utilities
```python
!pip install outlier_utils
!pip install iteration-utilities
```

### Import Gini PCA


```python
from Gini_PCA import GiniPca
```

### Import data and plot utilities: example on iris data


```python
from sklearn.datasets import load_iris
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
iris = load_iris()
x = iris.data
```

### Run the model by setting your own Gini parameter in (0,10] and != 1


```python
gini_param = 6
model = GiniPca(gini_param)
```

### Otherwise find the optimal Gini parameter: Grid search


```python
parameter = model.optimal_gini_param(x)
print(parameter)
```

    0.1
    

### Project the data x onto the new subspace


```python
scores = model.project(x)
```

### 3D plot


```python
y = iris.target
model.plot3D(x, y) 
```


![png](output_14_0.png)


### Absolute contributions (cos2) in %


```python
model.act(x)*100
```




    array([[ 4.14204577e-01,  3.36374074e-01,  1.18452709e+00,
            -6.10196220e-02],
           [ 6.03226665e-01, -9.35206328e-02, -1.40846480e-01,
             6.88762710e-03],
           [ 1.73121668e+00, -8.75352630e-03, -8.74836712e-01,
            -8.07322629e-01],
           [ 1.09951951e+00,  3.01913547e-02, -1.76259247e+00,
             2.33765060e+00],
           [ 5.14220524e-01,  3.79632062e-01,  4.06749751e-01,
             1.10654297e-02],
           [-1.90812939e-01,  8.13731181e-01, -1.25608092e-01,
             1.31341783e-01],
           [ 1.13880549e+00, -6.52441066e-03,  1.20092197e+00,
             2.04298817e-01],
           [ 2.67682005e-01,  1.82295515e-01,  2.43673177e-01,
             9.02742449e-01],
           [ 2.96721924e+00,  8.07093798e-01, -2.65829523e+00,
             2.44450172e+00],
           [ 2.60069307e+00, -4.07652311e-02,  1.31413208e+01,
             1.17693860e+01],
           [ 1.19382089e-01,  6.07365399e-01,  1.73144080e+00,
             5.62594023e-01],
           [ 4.93919359e-01,  8.41556503e-02, -7.46731091e-01,
             2.86666778e+00],
           [ 3.08453099e+00, -3.85696329e-02,  1.15673454e+01,
             7.81694984e+00],
           [ 1.57521734e+01,  1.86953680e+00, -5.09328398e+00,
             1.45850765e+00],
           [ 2.05444079e+00,  1.53314583e+00,  1.01960941e+01,
             4.82246939e+00],
           [-1.45682502e-01,  1.51174397e+00,  2.47136274e-01,
            -5.67657970e-03],
           [ 6.70825733e-01,  9.83778814e-01,  9.51501935e-01,
             3.90541593e+00],
           [ 1.98057942e-01,  3.41433445e-01,  7.82633428e-02,
             1.16451469e-01],
           [-1.92894869e-01,  8.06353304e-01,  5.96296370e-01,
             1.45905695e-01],
           [-1.78962334e-02,  6.21254465e-01, -9.94633302e-02,
             5.93583684e-02],
           [ 1.41168273e-02,  2.80027916e-01,  1.84688989e+00,
             1.13535410e+00],
           [-5.26463837e-02,  5.22421366e-01, -1.17031123e-01,
             7.29152324e-03],
           [ 1.02924780e+01,  5.44831397e-01, -4.86087754e-01,
            -6.26104848e+00],
           [-1.53001342e-01,  1.24581359e-01, -2.86278901e-01,
            -2.55705833e-01],
           [ 4.27196425e-01,  7.96231346e-02, -5.85846581e-01,
             5.24751208e+00],
           [ 1.63554360e-01, -1.01572223e-01,  3.66941043e-01,
             7.43057357e-01],
           [-5.20771813e-02,  1.81750257e-01, -4.04012822e-01,
            -3.70317950e-02],
           [ 1.46033923e-01,  3.50237089e-01,  1.28619315e+00,
             5.96827735e-01],
           [ 3.63110291e-01,  2.62241139e-01,  1.93317368e+00,
            -3.39004656e-02],
           [ 6.86423769e-01, -5.18321142e-03, -1.31428889e+00,
             2.96098649e+00],
           [ 4.71148589e-01, -3.84500519e-02, -1.35698886e+00,
             1.92734699e+00],
           [-9.92128165e-02,  2.97252861e-01, -4.06794411e-03,
             1.93133967e-01],
           [ 2.43963157e+00,  8.56111759e-01,  8.74789695e+00,
             2.21306359e+01],
           [ 3.26063592e-01,  1.24125626e+00,  1.81877356e+00,
            -2.33680489e-01],
           [ 3.83248611e-01, -5.08150222e-02, -5.35515056e-01,
             6.61145421e-01],
           [ 2.51814715e+00,  3.92148725e-02,  4.44972582e+00,
             4.22964974e+00],
           [ 8.78239582e-01,  5.04896594e-01,  5.19712078e+00,
             1.53307319e+00],
           [ 3.03946944e+00,  2.54967548e-01,  7.44498859e+00,
             1.48617155e+01],
           [ 3.76807702e+00,  5.06533015e-01, -1.34044923e+00,
             2.82164255e-01],
           [ 1.81802262e-01,  2.20294851e-01,  9.19521642e-01,
             6.37560865e-01],
           [ 9.18748712e-01,  3.37265567e-01,  2.93559584e-01,
             1.06688196e+00],
           [ 1.87730878e+00,  4.74792229e+00, -5.11843532e+00,
             3.90855047e+00],
           [ 3.85230994e+00,  1.30577611e-01,  1.87005913e+00,
             4.79536568e-01],
           [-6.47191893e-02,  2.71634344e-01,  2.86683312e-01,
            -4.06862575e-01],
           [-1.56498104e-01,  5.99093504e-01, -7.14232531e-03,
             6.96777667e-01],
           [ 5.52691441e-01, -6.42039434e-02, -1.63964523e+00,
             1.87356619e-01],
           [ 1.10615122e-01,  6.00212032e-01,  4.05251078e-01,
             2.18049265e+00],
           [ 1.37845819e+00,  4.87917552e-03, -1.24989327e+00,
             1.05147300e+00],
           [ 1.35936813e-01,  5.79425964e-01,  1.34623935e+00,
             7.21865227e-01],
           [ 4.94045266e-01,  1.06148821e-01,  6.56985569e-01,
            -2.67525115e-04],
           [ 2.88623139e-01,  3.45906566e-01,  6.33504516e-02,
             3.57706580e-02],
           [ 1.98427123e-01,  2.35316684e-01, -1.08514754e-02,
            -2.82325280e-02],
           [ 3.35016334e-01,  2.09481169e-01, -2.81486303e-02,
             4.19062744e-02],
           [ 5.11816549e-02,  2.86569766e+00, -3.58672113e-01,
             3.83005550e-01],
           [ 2.66744173e-01, -7.64436004e-02,  1.46985562e-01,
            -5.47449066e-02],
           [ 7.74813342e-02, -1.29320643e-01,  1.47209671e-02,
             4.28788771e-01],
           [ 2.22663449e-01,  3.22028289e-01,  1.39406750e-01,
             4.31687422e-02],
           [-6.85057634e-02,  1.86316126e+00,  3.73290985e-01,
             1.31904251e-02],
           [ 2.15423751e-01, -2.56468729e-02,  3.42100028e-01,
             1.56971758e-01],
           [-1.02839681e-02, -1.29478622e-02,  6.04380459e-01,
            -7.18299493e-04],
           [-3.98933439e-01,  2.99259099e+01, -4.61055901e-01,
            -6.54574995e-01],
           [ 1.04425651e-01, -4.38514857e-02,  1.46342141e-01,
            -5.60069808e-02],
           [ 1.03147772e-01,  6.90008071e+00,  9.61033089e+00,
            -7.77835517e-01],
           [ 1.74410603e-01, -8.55401284e-02,  5.84163192e-04,
             2.83549562e-01],
           [-1.38063687e-02, -1.22525399e-01,  7.93301030e-02,
            -3.55590966e-02],
           [ 2.12607417e-01,  1.83285148e-01,  6.73069875e-02,
            -8.00945434e-02],
           [ 8.92587493e-02, -8.89962899e-02,  7.13542122e-01,
             2.11377577e-01],
           [ 5.67626312e-03, -4.80532464e-02,  3.62695038e-01,
             3.93079670e-01],
           [ 4.84407637e-01,  6.63090787e+00,  4.27078156e+00,
             2.84363938e+00],
           [-6.45237323e-03,  5.13892901e-01,  2.63810812e-01,
            -7.93051806e-02],
           [ 2.19878293e-01,  1.34575110e-01,  8.41614563e-01,
            -5.83639634e-02],
           [ 8.47738666e-02, -1.03555246e-01,  1.46251656e-01,
            -1.55928193e-02],
           [ 3.29524881e-01,  3.90890444e-01,  4.70336351e-01,
            -2.45497841e-02],
           [ 1.33656546e-01, -1.08613684e-01,  1.58390557e-01,
             7.92274431e-01],
           [ 1.50367557e-01, -4.61848896e-02,  2.43697182e-01,
            -4.91999385e-03],
           [ 2.06368102e-01,  5.97725898e-02,  1.01689969e-01,
            -6.89782591e-02],
           [ 3.13573316e-01, -5.27189377e-02,  4.87230476e-01,
             2.70495679e-02],
           [ 3.76481038e-01,  6.72654354e-02, -2.23591558e-02,
            -1.27296194e-01],
           [ 1.59922949e-01, -9.32369926e-02,  4.79579041e-02,
             3.55258066e-03],
           [-4.48690264e-02,  1.11791493e-01,  5.48118679e-01,
             2.99467782e-03],
           [-2.38856848e-02,  1.39393225e+00,  3.33382010e-01,
            -1.08772351e-01],
           [-5.11380861e-02,  1.39220748e+00,  7.38432351e-01,
            -1.98160604e-01],
           [ 2.44394735e-02, -4.92991037e-02,  1.19357439e-01,
            -2.30621332e-04],
           [ 2.82464934e-01, -4.77511255e-02, -5.69656836e-02,
             1.51257575e-01],
           [ 5.93815200e-02, -1.10543556e-01,  1.43156141e+00,
             3.66862185e-01],
           [ 1.45562963e-01,  3.76002281e-01,  4.75800787e-01,
             3.81951333e-02],
           [ 2.77521820e-01,  1.77365364e-01, -3.52640391e-02,
            -3.42613278e-02],
           [ 2.73561913e-01,  2.33146989e+00,  3.67647392e+00,
             3.87985839e-01],
           [ 1.72409889e-02, -8.46496512e-02,  2.44036095e-01,
             1.87218091e-01],
           [ 2.69844775e-02,  5.42154321e-01, -2.23283011e-01,
             2.82919146e-02],
           [ 3.49971828e-02,  1.50240238e-01, -1.06434096e-01,
             3.60475609e-01],
           [ 1.54194034e-01, -2.21402642e-02,  1.31484550e-02,
             2.56974439e-01],
           [ 4.02061029e-02,  1.04367138e-01,  2.24166475e-01,
            -3.30372980e-03],
           [-1.24924044e-01,  3.31122235e+00, -3.88251250e-01,
             2.95468928e-02],
           [ 4.35426358e-02, -3.91478327e-02, -4.30518587e-02,
             6.95427635e-02],
           [ 1.96416924e-02, -7.44253881e-02,  4.21226672e-02,
             5.19291928e-01],
           [ 4.33565687e-02, -1.21019483e-01,  5.50979796e-02,
             1.65276004e-01],
           [ 1.20816595e-01, -6.97302450e-02,  8.61019470e-02,
             5.15103933e-02],
           [-1.05047598e-01,  6.49656398e-01, -9.02258632e-02,
             1.79166167e-01],
           [ 4.10213081e-02, -1.27377213e-01, -5.74742962e-03,
             3.87687389e-02],
           [ 6.03615713e-01,  3.02290997e-01,  1.52219881e+00,
            -3.43878693e-01],
           [ 3.21135270e-01, -4.63014912e-02,  1.51345905e-01,
            -5.29478081e-02],
           [ 6.74031775e-01,  1.18263816e-01,  5.28011655e-03,
            -1.94836524e-01],
           [ 4.18603517e-01, -7.19504729e-02,  1.22665039e-01,
             3.22800159e-01],
           [ 5.76750410e-01,  2.57518850e-02,  4.02535484e-01,
            -1.88167958e-01],
           [ 8.45744066e-01,  1.84824431e-01, -1.21522909e-01,
             1.59418575e-01],
           [ 4.09107388e-02,  8.98190880e-01,  4.94658811e+00,
            -1.57067046e-02],
           [ 6.89178468e-01,  4.18679571e-02,  2.30421502e-02,
             5.00621574e-01],
           [ 6.31831449e-01,  3.39416763e-01,  3.50916739e-01,
            -5.47046069e-02],
           [ 7.64154898e-01,  8.44444833e-01,  5.39454283e-01,
            -4.99806621e-01],
           [ 4.14421110e-01,  2.46707750e-01,  3.12688688e-01,
            -3.27781441e-01],
           [ 4.68371202e-01, -4.63902092e-02, -9.55568704e-02,
            -5.76888153e-02],
           [ 5.67346779e-01,  7.80490549e-02,  9.55717825e-02,
            -3.19909093e-01],
           [ 3.57141731e-01,  5.05792821e-01, -7.09764541e-01,
             2.35330937e-01],
           [ 4.25856948e-01, -1.24682234e-01,  1.09984434e+00,
            -3.96330050e-01],
           [ 4.96589540e-01,  2.26224338e-01,  7.87065128e-01,
            -5.49631881e-01],
           [ 4.30472843e-01,  2.71601967e-02,  7.98007774e-02,
             1.98438694e-01],
           [ 8.23949175e-01,  1.17085210e+00,  5.05864443e-02,
             4.40363198e-01],
           [ 1.08894507e+00,  2.90572969e-02,  4.10291794e-01,
             6.03807835e-03],
           [ 5.30978967e-01,  7.03644799e+00,  1.16302769e+00,
            -1.00233750e+00],
           [ 6.42788268e-01,  3.14182351e-01,  3.20180286e-01,
            -4.91486538e-01],
           [ 2.59008216e-01, -1.31029651e-01,  1.18768294e+00,
            -2.10368358e-01],
           [ 8.92858725e-01,  1.33306822e-02,  1.35600060e-01,
             2.02445695e-01],
           [ 3.64618249e-01, -4.67291317e-02, -7.34198219e-02,
            -3.95024847e-02],
           [ 5.43519269e-01,  3.86330650e-01,  3.73236656e-01,
            -9.45864719e-02],
           [ 5.93345486e-01,  3.57724796e-01, -1.08109397e-01,
             5.13870031e-01],
           [ 3.13599030e-01, -9.94978785e-02,  2.27013330e-02,
            -1.26590739e-01],
           [ 2.83290095e-01, -2.34431254e-02,  3.39536996e-01,
            -1.18457166e-01],
           [ 5.38507640e-01, -9.05154379e-02,  7.26445458e-02,
            -1.41038385e-01],
           [ 5.37252856e-01,  1.30734002e-01, -4.21974227e-02,
             5.87043483e-01],
           [ 7.35569323e-01, -8.52108019e-03,  1.31608146e-01,
             4.99680398e-02],
           [ 7.67419889e-01,  1.21815191e+00, -2.20828303e-01,
             4.49651816e-01],
           [ 5.65231531e-01, -8.99486127e-02,  1.06737497e-01,
            -2.14647866e-01],
           [ 2.94269316e-01, -9.62814941e-02,  1.14909381e-02,
             3.04178661e-01],
           [ 3.22524422e-01,  9.55944845e-02,  9.53991767e-03,
             7.18410734e-01],
           [ 8.61434589e-01,  2.12768339e-01, -1.20431136e-01,
            -5.26168519e-01],
           [ 5.21109430e-01,  4.23924162e-01,  1.38698626e+00,
            -4.48479781e-01],
           [ 4.00297448e-01,  1.08912390e-01,  2.11131942e-01,
             3.20161166e-01],
           [ 2.53284542e-01, -3.64840094e-02,  4.50939613e-01,
            -1.43735466e-01],
           [ 5.59515988e-01,  2.05631543e-01,  9.19291560e-02,
            -4.10889077e-01],
           [ 6.27960561e-01,  1.68251321e-01,  4.99827873e-01,
            -5.91826315e-01],
           [ 5.72756470e-01,  2.14736807e-01,  1.88071367e-01,
            -6.28620648e-01],
           [ 3.21135270e-01, -4.63014912e-02,  1.51345905e-01,
            -5.29478081e-02],
           [ 6.49848047e-01,  2.90262633e-01,  4.28004519e-01,
            -3.23862594e-01],
           [ 6.47812733e-01,  3.91626606e-01,  7.80598556e-01,
            -6.67188838e-01],
           [ 5.63649600e-01,  6.97839459e-02,  2.48976665e-01,
            -5.66859641e-01],
           [ 4.61166397e-01,  3.88601902e-01, -2.93092307e-01,
             4.02335843e-01],
           [ 4.48744248e-01,  3.48522916e-02,  1.80699490e-01,
            -3.00945043e-01],
           [ 4.50616493e-01,  4.05497389e-01,  1.40458978e+00,
            -4.08020466e-01],
           [ 2.72174571e-01, -5.61552526e-02,  6.66408180e-01,
             1.19623781e-01]])



### Relative contributions 


```python
model.rct(x)
```




    array([[9.83548621e-03, 6.62780300e-03, 7.31376244e-03, 3.55074089e-03],
           [9.79396153e-03, 3.63358371e-03, 8.43032568e-03, 3.07092805e-04],
           [1.06682515e-02, 4.60316819e-04, 3.77033540e-03, 2.55039508e-03],
           [1.04770642e-02, 2.80338240e-03, 2.56572182e-03, 7.13775902e-03],
           [1.01898345e-02, 8.19383690e-03, 4.86520485e-03, 5.80896914e-03],
           [8.30159091e-03, 1.52459327e-02, 4.46401173e-03, 2.61005226e-03],
           [1.06020351e-02, 3.00105569e-03, 1.50962919e-03, 3.81757834e-03],
           [9.80989222e-03, 4.32593652e-03, 6.34627377e-03, 5.86495062e-03],
           [1.09226562e-02, 7.28351809e-03, 1.34211922e-03, 4.94671582e-03],
           [1.00976884e-02, 1.78461923e-03, 9.06928902e-03, 8.06161896e-03],
           [9.14272028e-03, 1.14552554e-02, 1.01268257e-02, 4.59214222e-03],
           [1.01386465e-02, 3.59010393e-03, 2.93022751e-03, 1.04373886e-02],
           [1.04032812e-02, 4.00408752e-03, 8.57605017e-03, 5.82952025e-03],
           [1.21359304e-02, 5.61707396e-03, 1.34012152e-03, 4.75826698e-03],
           [8.97232841e-03, 1.87081716e-02, 1.46187524e-02, 3.50012884e-03],
           [8.42712847e-03, 2.59370343e-02, 5.41115898e-03, 1.57750034e-04],
           [8.96396434e-03, 1.54107290e-02, 5.41251136e-03, 6.48256462e-03],
           [9.47334041e-03, 6.65099007e-03, 5.57857727e-03, 8.22044673e-04],
           [7.81504073e-03, 1.43513452e-02, 1.18266758e-02, 2.42532583e-03],
           [9.62927047e-03, 1.23498429e-02, 2.76416161e-03, 4.77686865e-03],
           [8.49001015e-03, 5.63280531e-03, 1.22298667e-02, 5.81269155e-03],
           [9.15995020e-03, 1.04596793e-02, 1.88807335e-03, 7.04503285e-04],
           [1.18409033e-02, 6.96936630e-03, 5.44138222e-04, 1.31491977e-03],
           [8.03791981e-03, 2.74706562e-03, 3.11502604e-03, 4.96532589e-03],
           [9.64186646e-03, 3.46650664e-03, 2.21885279e-03, 1.72568513e-02],
           [9.21560098e-03, 3.36866516e-03, 9.54553654e-03, 3.70375937e-03],
           [8.92000727e-03, 4.33111155e-03, 2.63877852e-03, 6.07466295e-04],
           [9.42271901e-03, 6.93392065e-03, 8.66609821e-03, 4.67425324e-03],
           [9.48113790e-03, 5.06176910e-03, 9.76232003e-03, 1.29251265e-03],
           [1.01714714e-02, 5.83914108e-04, 3.05896067e-03, 9.36985773e-03],
           [9.81712313e-03, 2.14994801e-03, 5.50751827e-03, 7.11162949e-03],
           [8.09690527e-03, 5.76157763e-03, 9.23374614e-03, 7.47918802e-03],
           [1.04279116e-02, 1.83908375e-02, 5.24670187e-03, 1.56985570e-02],
           [9.59701215e-03, 2.14105245e-02, 7.65792672e-03, 6.71227797e-03],
           [9.73554265e-03, 1.76143216e-03, 7.33410385e-03, 3.68883339e-03],
           [1.00923234e-02, 6.22832516e-04, 8.77584234e-03, 3.17168477e-03],
           [9.01238422e-03, 8.05826908e-03, 1.39087301e-02, 3.32098083e-03],
           [1.07991542e-02, 7.82333309e-03, 5.01092934e-03, 1.13313966e-02],
           [1.11954241e-02, 5.32896835e-03, 7.20147209e-04, 3.78214797e-03],
           [9.56271838e-03, 4.67325326e-03, 7.93573445e-03, 4.71530875e-03],
           [9.88610761e-03, 6.34487242e-03, 4.22624150e-03, 1.94555702e-03],
           [9.83588315e-03, 1.83519190e-02, 6.58810114e-03, 9.50038406e-03],
           [1.14097730e-02, 1.50226706e-03, 9.98046628e-04, 5.99932071e-03],
           [8.30289014e-03, 6.29083632e-03, 1.69068874e-03, 8.24445106e-03],
           [8.60475124e-03, 1.22082336e-02, 8.04768003e-05, 9.49669996e-03],
           [9.67898957e-03, 3.95771339e-03, 5.10567983e-03, 2.91605089e-03],
           [9.82582291e-03, 1.22854567e-02, 4.26222187e-03, 1.14228084e-02],
           [1.07498320e-02, 8.48832662e-04, 1.94374982e-03, 5.97319117e-03],
           [9.38989412e-03, 1.11079387e-02, 8.53736505e-03, 5.74178410e-03],
           [9.86831111e-03, 2.45378497e-03, 7.44249560e-03, 2.48321003e-03],
           [4.99267047e-03, 6.40544384e-03, 1.14434620e-02, 9.22448551e-04],
           [3.54058652e-03, 4.42712862e-03, 6.45762589e-04, 1.09879420e-03],
           [5.54600361e-03, 4.08556532e-03, 8.50366325e-03, 1.13702693e-03],
           [7.28333840e-04, 1.57592565e-02, 1.27151635e-03, 3.34949458e-03],
           [4.38205160e-03, 2.92015631e-03, 5.43448603e-03, 4.40962733e-03],
           [1.51477595e-03, 5.70386531e-03, 3.57370413e-03, 1.12599246e-02],
           [3.87957073e-03, 5.93395139e-03, 4.01222999e-03, 1.33295692e-03],
           [3.10747455e-03, 1.57109739e-02, 4.80194745e-03, 1.86322022e-03],
           [3.79775937e-03, 7.05863045e-04, 9.63522013e-03, 4.29488830e-03],
           [2.45333115e-04, 9.08341804e-03, 1.09743463e-02, 2.11216327e-03],
           [2.10041611e-03, 2.30994579e-02, 2.50348914e-04, 8.25541304e-04],
           [2.02228621e-03, 1.01255911e-03, 4.87197223e-03, 4.38722021e-03],
           [9.84940107e-04, 1.60055846e-02, 1.27404395e-02, 2.91206637e-03],
           [3.08962934e-03, 2.46045881e-03, 2.84393331e-04, 7.94346634e-03],
           [3.29912574e-04, 3.76703955e-03, 3.88813754e-03, 6.94023512e-03],
           [3.86154335e-03, 3.57374025e-03, 8.24555161e-03, 3.55667485e-03],
           [1.77754477e-03, 2.17810664e-03, 1.03517290e-02, 5.88116808e-03],
           [1.20313438e-04, 7.17466401e-03, 5.02890861e-03, 1.30274362e-02],
           [4.11798355e-03, 1.54010113e-02, 6.05781042e-03, 9.88537413e-03],
           [1.28726214e-04, 1.15904135e-02, 2.30724574e-03, 4.19045320e-03],
           [3.88793480e-03, 2.63650879e-03, 1.32184710e-02, 1.64947886e-03],
           [1.67550451e-03, 4.10860284e-03, 3.96976312e-03, 4.70441400e-03],
           [4.70600741e-03, 9.47843902e-03, 4.12148070e-03, 1.38335998e-03],
           [2.47251222e-03, 4.42018358e-03, 4.04507393e-03, 1.55804511e-02],
           [2.80663163e-03, 1.27689925e-03, 7.16767350e-03, 2.25290604e-04],
           [3.72154399e-03, 1.31307285e-03, 7.51518786e-03, 3.51561934e-03],
           [5.09261403e-03, 1.98379133e-03, 1.14638034e-02, 1.06054105e-03],
           [6.04871536e-03, 1.48275621e-03, 2.47634357e-03, 4.14469260e-03],
           [2.87341459e-03, 2.70219030e-03, 3.13478936e-03, 1.74014206e-04],
           [1.01324607e-03, 9.18813683e-03, 5.72129431e-03, 5.70433622e-04],
           [4.34318939e-04, 1.38098818e-02, 1.81400690e-03, 1.95835448e-03],
           [9.62058093e-04, 1.37918698e-02, 3.78631698e-03, 4.05798583e-03],
           [5.13418317e-04, 7.04589169e-03, 2.03278809e-03, 2.64443389e-04],
           [4.44346947e-03, 6.75289910e-03, 4.57453015e-03, 7.22298122e-03],
           [1.28319709e-03, 2.87274013e-03, 1.35306503e-02, 8.18045183e-03],
           [2.69968803e-03, 6.88774998e-03, 9.16545912e-03, 1.34416048e-03],
           [4.72046922e-03, 3.47333002e-03, 5.79899172e-03, 1.10999776e-03],
           [3.36809797e-03, 1.31455190e-02, 1.04956694e-02, 3.45401272e-03],
           [3.90879742e-04, 2.05968438e-03, 5.93285901e-03, 5.53412234e-03],
           [5.13984899e-04, 1.19325553e-02, 2.98971018e-03, 1.13232185e-03],
           [7.07038061e-04, 1.02071881e-02, 3.06212156e-03, 1.34416670e-02],
           [2.81686151e-03, 5.05909069e-04, 9.06365341e-04, 6.77889849e-03],
           [7.86186145e-04, 9.00044143e-03, 2.65476010e-03, 9.00124461e-04],
           [2.75312624e-03, 1.72770078e-02, 2.35338985e-03, 3.95008029e-04],
           [8.77996511e-04, 7.84093541e-03, 3.59269316e-03, 4.48151745e-03],
           [4.41501140e-04, 1.77675380e-03, 2.84533807e-03, 1.10304203e-02],
           [9.10821407e-04, 3.66691738e-03, 3.72142632e-03, 5.54904831e-03],
           [2.31228395e-03, 1.97153274e-03, 3.98875215e-03, 2.07399315e-03],
           [2.85493562e-03, 1.29562054e-02, 3.50593345e-03, 1.05197254e-02],
           [8.52402521e-04, 5.53906893e-03, 2.62520449e-03, 2.16730773e-03],
           [9.29159654e-03, 5.60704671e-03, 2.27115203e-02, 8.47110834e-03],
           [5.03555918e-03, 7.37797140e-03, 1.29590070e-02, 3.59609173e-03],
           [9.97633411e-03, 2.59397959e-03, 2.40678590e-04, 5.77601441e-03],
           [6.52290042e-03, 2.04386893e-03, 6.18033684e-03, 8.61142828e-03],
           [8.68984353e-03, 5.74465271e-04, 1.12755029e-02, 5.52410294e-03],
           [1.23713568e-02, 4.04216965e-03, 6.04675043e-03, 4.38785574e-03],
           [1.30749185e-03, 1.41297030e-02, 2.06528395e-02, 3.59841760e-04],
           [1.01537923e-02, 1.14090486e-03, 8.05439556e-03, 1.30270891e-02],
           [8.27148036e-03, 8.39040271e-03, 3.13964372e-03, 4.12482374e-03],
           [1.13602310e-02, 1.44317503e-02, 1.12207899e-02, 1.32189719e-02],
           [6.59204949e-03, 4.64318610e-03, 7.86345204e-03, 1.04734386e-02],
           [6.84978892e-03, 5.37646912e-03, 3.89649277e-03, 5.94763456e-03],
           [8.57243917e-03, 1.71682573e-03, 4.06056098e-03, 1.14197057e-02],
           [5.19928673e-03, 1.14876033e-02, 1.43283341e-02, 1.13095624e-02],
           [6.73911370e-03, 5.34868544e-03, 2.24940298e-02, 2.43514332e-02],
           [7.76249976e-03, 4.28303236e-03, 1.51327180e-02, 1.78958450e-02],
           [6.74448027e-03, 6.05314305e-04, 3.62338750e-03, 5.14757668e-03],
           [1.22888740e-02, 1.96782795e-02, 1.20887432e-03, 1.00072735e-02],
           [1.42683002e-02, 3.34113934e-03, 6.89085371e-03, 3.12224009e-03],
           [4.45160266e-03, 1.63016403e-02, 1.69326452e-03, 3.77968072e-03],
           [9.66074237e-03, 5.85481970e-03, 8.13391430e-03, 1.45514375e-02],
           [4.46499612e-03, 6.05366900e-03, 1.82579606e-02, 9.10731562e-03],
           [1.26363271e-02, 4.98398946e-04, 1.08524652e-02, 7.66698092e-03],
           [5.57809586e-03, 5.58217654e-03, 2.80226864e-03, 9.51782399e-03],
           [8.33492864e-03, 7.02716273e-03, 8.70156223e-03, 2.39799623e-03],
           [9.08831497e-03, 6.65723734e-03, 4.59901885e-03, 1.06830274e-02],
           [5.05815419e-03, 3.97494355e-03, 5.01370133e-03, 9.53274996e-03],
           [4.76222477e-03, 5.36758103e-04, 8.55848075e-03, 3.89278113e-03],
           [7.96368612e-03, 3.54034163e-03, 8.93733476e-03, 6.76515667e-03],
           [8.24718561e-03, 2.86656011e-03, 1.02618328e-02, 1.26651173e-02],
           [1.05390997e-02, 3.19543780e-04, 9.24201780e-03, 1.84976680e-03],
           [1.15621500e-02, 2.04501362e-02, 6.15179210e-03, 9.63409819e-03],
           [8.32583191e-03, 3.51715457e-03, 1.06725199e-02, 1.11379422e-02],
           [4.71567071e-03, 3.82078528e-03, 1.06994013e-03, 9.25542752e-03],
           [4.90149297e-03, 8.57130261e-03, 1.58773243e-04, 2.50760952e-02],
           [1.25148554e-02, 4.64185600e-03, 5.35146531e-03, 1.68731284e-02],
           [8.15990285e-03, 7.66200667e-03, 2.08869325e-02, 1.20823533e-02],
           [6.39013196e-03, 2.17134820e-03, 6.07194509e-03, 7.40580492e-03],
           [4.34945758e-03, 8.42875753e-04, 9.91081652e-03, 5.01629347e-03],
           [8.54684518e-03, 4.01869222e-03, 3.09307232e-03, 1.37339154e-02],
           [9.47012161e-03, 3.31122173e-03, 1.19517990e-02, 2.00066799e-02],
           [8.77435670e-03, 4.18866364e-03, 5.85206793e-03, 2.92989492e-02],
           [5.03555918e-03, 7.37797140e-03, 1.29590070e-02, 3.59609173e-03],
           [9.74475525e-03, 5.42510477e-03, 1.01976248e-02, 8.85548718e-03],
           [9.78351182e-03, 7.11991098e-03, 1.56423029e-02, 1.98891385e-02],
           [8.55277685e-03, 1.53948040e-03, 8.40901727e-03, 2.58350976e-02],
           [6.32018395e-03, 9.42688986e-03, 3.05638489e-03, 1.38346281e-02],
           [6.97199179e-03, 7.75285721e-04, 6.38238311e-03, 1.04174571e-02],
           [7.21939650e-03, 7.37390106e-03, 2.02669581e-02, 1.11062343e-02],
           [4.59906381e-03, 1.31378979e-03, 1.22116519e-02, 2.95281106e-03]])



### Feature importance in Gini PCA (factors loadings)

* U-statitics > 2.57: significance of 1% 
* U-statitics > 1.96: significance of 5% 
* U-statitics > 1.65: significance of 10% 


```python
model.u_stat(x)
```




    array([[-40.30577176,   0.94614065, -48.12517983, -45.22470418],
           [ -3.12762227, -23.76476321,   1.35866338,   1.26459391]])



### Feature importance in standard PCA (factors loadings)

* U-statitics > 2.57: significance of 1% 
* U-statitics > 1.96: significance of 5% 
* U-statitics > 1.65: significance of 10% 


```python
model.u_stat_pca(x)
```




    array([[11.78270546, -5.86022403, 15.57293717, 15.58145032],
           [-4.06529552, -7.43327168, -0.27455139, -0.79030779]])



[Stack Abuse](http://stackabuse.com)

### Hotelling T2 to detect outliers in the new subspace: component 1 & component 2


```python
model.hotelling(x)
```




    (array([1.67552821e+00, 1.66141017e+00, 1.97127207e+00, 1.90125025e+00,
            1.79843331e+00, 1.19366575e+00, 1.94687718e+00, 1.66681941e+00,
            2.06641054e+00, 1.76605413e+00, 1.44780790e+00, 1.78041007e+00,
            1.87456606e+00, 2.55097518e+00, 1.39434550e+00, 1.23004020e+00,
            1.39174708e+00, 1.55441280e+00, 1.05784629e+00, 1.60600483e+00,
            1.24846536e+00, 1.45326998e+00, 2.42845324e+00, 1.11904465e+00,
            1.61020919e+00, 1.47098215e+00, 1.37813097e+00, 1.53784498e+00,
            1.55697272e+00, 1.79195725e+00, 1.66927755e+00, 1.13552891e+00,
            1.88345289e+00, 1.59526254e+00, 1.64164937e+00, 1.76417795e+00,
            1.40682304e+00, 2.01994506e+00, 2.17090678e+00, 1.58388195e+00,
            1.69281985e+00, 1.67566346e+00, 2.25483146e+00, 1.19403941e+00,
            1.28243900e+00, 1.62263232e+00, 1.67223744e+00, 2.00153611e+00,
            1.52714919e+00, 1.68673067e+00, 4.31743573e-01, 2.17125335e-01,
            5.32746215e-01, 9.18800143e-03, 3.32594491e-01, 3.97426552e-02,
            2.60691832e-01, 1.67253509e-01, 2.49812960e-01, 1.04249126e-03,
            7.64136174e-02, 7.08345788e-02, 1.68027251e-02, 1.65338060e-01,
            1.88520165e-03, 2.58274724e-01, 5.47269406e-02, 2.50719636e-04,
            2.93717141e-01, 2.87008046e-04, 2.61817109e-01, 4.86240670e-02,
            3.83588245e-01, 1.05885616e-01, 1.36436606e-01, 2.39886821e-01,
            4.49201917e-01, 6.33703889e-01, 1.43006791e-01, 1.77823820e-02,
            3.26721423e-03, 1.60310759e-02, 4.56565188e-03, 3.41982968e-01,
            2.85198219e-02, 1.26237167e-01, 3.85949442e-01, 1.96485048e-01,
            2.64634464e-03, 4.57573428e-03, 8.65855985e-03, 1.37433013e-01,
            1.07055959e-02, 1.31284159e-01, 1.33519795e-02, 3.37616556e-03,
            1.43689997e-02, 9.26066997e-02, 1.41173348e-01, 1.25848930e-02,
            1.49534280e+00, 4.39193077e-01, 1.72386022e+00, 7.36956025e-01,
            1.30792846e+00, 2.65090853e+00, 2.96099761e-02, 1.78573342e+00,
            1.18502241e+00, 2.23529272e+00, 7.52663742e-01, 8.12670424e-01,
            1.27282560e+00, 4.68217469e-01, 7.86621195e-01, 1.04367018e+00,
            7.87874516e-01, 2.61567789e+00, 3.52618060e+00, 3.43236025e-01,
            1.61651999e+00, 3.45304508e-01, 2.76567917e+00, 5.38929583e-01,
            1.20327210e+00, 1.43062832e+00, 4.43143318e-01, 3.92807577e-01,
            1.09847037e+00, 1.17807140e+00, 1.92383181e+00, 2.31545998e+00,
            1.20064704e+00, 3.85165181e-01, 4.16118328e-01, 2.71276237e+00,
            1.15326750e+00, 7.07261031e-01, 3.27665167e-01, 1.26523661e+00,
            1.55335668e+00, 1.33349272e+00, 4.39193077e-01, 1.64475778e+00,
            1.65786676e+00, 1.26699342e+00, 6.91862058e-01, 8.41925785e-01,
            9.02738295e-01, 3.66352321e-01]),
     array([ 2.25953689,  1.82916925,  1.96091334,  1.99498481,  2.69614594,
             4.33536779,  2.0558534 ,  1.90921755,  2.77140385,  1.7973587 ,
             3.21625819,  1.94311442,  2.07924026,  2.96140099,  6.12768809,
            10.33777095,  4.6005795 ,  2.14340655,  3.84167213,  3.66196647,
             1.670031  ,  2.92603375,  3.07034235,  1.21379317,  1.76223717,
             1.61488229,  1.6230737 ,  2.17903337,  1.89371362,  1.78455089,
             1.72070961,  1.57773525,  6.45398294,  7.79635847,  1.6726747 ,
             1.75759444,  2.27730809,  2.83575521,  2.54114955,  1.8691905 ,
             2.22697629,  6.22821093,  2.27027976,  1.72229114,  3.29344745,
             1.82399412,  3.70626075,  1.99786652,  3.18887559,  1.75700016,
             0.98482892,  0.48125541,  0.75535758,  3.37450913,  0.44591371,
             0.48033678,  0.73608789,  3.5109239 ,  0.25488792,  1.11908652,
             7.30637189,  0.08425243,  3.48810151,  0.24626266,  0.19416551,
             0.42960623,  0.11864637,  0.69778428,  3.50586153,  1.82066016,
             0.35425356,  0.27704259,  1.59842325,  0.36992965,  0.15761502,
             0.26164049,  0.4995151 ,  0.65924304,  0.24099225,  1.16164171,
             2.58754538,  2.59348665,  0.67725595,  0.95762384,  0.14015774,
             0.76825196,  0.5468356 ,  2.53679753,  0.06011489,  1.93397902,
             1.42040719,  0.13997887,  1.10835138,  4.17523123,  0.84636551,
             0.04613122,  0.19647965,  0.14465611,  2.41489728,  0.42825455,
             1.9113283 ,  1.17387273,  1.80346996,  0.78861688,  1.3036223 ,
             2.85452457,  2.73479628,  1.79138714,  2.13102587,  5.04257681,
             1.03975512,  1.19891965,  1.30422382,  2.2532989 ,  1.16900734,
             1.28524543,  0.78755183,  7.84543962,  3.65378475,  3.94195323,
             2.07017551,  0.83957976,  2.75048359,  0.95756309,  1.86434577,
             2.02157945,  0.65427329,  0.39407538,  1.26094332,  1.28151358,
             1.91230383,  7.96694888,  1.36021676,  0.58039931,  1.40886091,
             2.98653136,  1.9410419 ,  0.76640271,  0.33509305,  1.47558802,
             1.69150435,  1.56228953,  1.17387273,  2.03254129,  2.33366961,
             1.29060536,  1.89142219,  0.84442019,  1.63349324,  0.38728275]))


