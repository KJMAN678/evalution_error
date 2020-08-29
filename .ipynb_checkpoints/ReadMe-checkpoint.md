## 精度評価指標 比較

kaggleの[HousePrice](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)コンペ(回帰)のデータをもとに、下記4パターンについて、MSE、MAE、決定係数、RSMEの4つの精度評価指標を試した。

特徴量選択1 欠損値を含まない数値データを特徴量とする

特徴量選択2 1に加え、欠損値処理を行った数値データを特徴量とする

特徴量選択3 2に加え、ラベルエンコーディングしてobjectデータも特徴量とする

特徴量選択4 3に加え、外れ値を処理する

##### 1.MSE（Mean Squared Error） 平均二乗誤差

<div>[tex:\displaystyle{
MSE=\frac{1}N \sum_{i=1}^n (y_{test, i}- y_{pred, i})^ 2
}]</div>  

予測値と正解の差（残差）の二乗をサンプルごとに足し上げたものをサンプル数で割ったもの。

MSE が 0 に近いほど見積もられる予測誤差が小さい、すなわち予測精度が高い。

##### 2.MAE（Mean Absolute Error） 平均絶対誤差

<div>[tex:\displaystyle{
MAE=\frac{\sum_{i}|y_{test,i} - y_{pred,i}|}n
}]</div>  

残差の絶対値をサンプルごとに足し上げ、最後にサンプル数で割ったもの。

MSEと比べ残差が二乗されていない分、（予測の）外れ値の影響を受けにくい。

MAE も 0 に近いほど予測精度が高いことを表す。

##### 3.R2（Multiple R-Squared） 決定係数

<div>[tex:\displaystyle{
R^2=1-\frac{\sum{(y_{test,i}-y_{pred,i})^2}}{\sum{(y_{test,i}-\overline{y_{pred,i}})^2}}
}]</div>  

検証データの平均値で予測をした場合の残差平方和 SST（Sum of Squared Total）と、モデルの残差平方和 SSE（Sum of Squared Errors）の比率で、 R2=1−SSE/SST と定義される。

平均値予測という最もナイーブな予測に対して二乗誤差をどれだけ削れたかを示す指標で、誤差をすべてなくせば1.0となり、平均値予測と同じになれば0.0になる。 

R2 の範囲は、通常0〜１の値を取りますが、負になる可能性がある。

##### 4.RMSE（Root Mean Squared Error） 平均平方二乗誤差

<div>[tex:\displaystyle{
RMSE=\sqrt{\frac{\sum{(y^{test,i}-y ^{pred,i})^2}}{n}}
}]</div>  

実績と予測が近似する（誤差が小さい）ほど、RMSE は小さくなる。

逆に、実績と予測が乖離する（誤差が大きい）と、RMSE が大きくなる。

したがって、外れ値があると、RMSE が著しく大きくなる。

RMSE は外れ値の影響を受けやすい。

