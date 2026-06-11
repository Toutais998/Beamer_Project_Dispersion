<!-- 数学表达的光程差（OPD）与成像理论 -->

### **一、 光程与波前偏离的物理定义*

光程是衡量相位延迟的物理量，将介质中的传播路径等效至真空。马吕斯定律指出，理想成像系统中，物点到像点的所有光线光程均相等。

- **光程 (Optical Path Length, OPL)：** 光在折射率 $n$ 连续分布介质中的积分路径：

  $$OPL = \int n(s) ds$$

- **光程差 (Optical Path Difference, OPD)：** 两束光线的 OPL 之差。在成像系统中，常等效为**波像差函数 (Wave Aberration Function)** $W(x,y)$，即实际波前与理想参考球面波前的法向几何偏离量：

  $$OPD = OPL_{actual} - OPL_{ideal} \equiv W(x,y)$$

### **二、 从相位调制到像面光场 (干涉与衍射)**

光程差是评估像质的根本，因为它直接决定了光波的相位分布，进而通过干涉决定像面的能量重组。

- **相位差 ($\Delta\phi$)：**

  $$\Delta\phi = k \cdot OPD = \frac{2\pi}{\lambda} W(x,y)$$

- **广义光瞳函数 (Generalized Pupil Function)：** 结合振幅透过率 $A(x,y)$ 与相位调制，表征系统的实际出瞳波前：

  $$P(x,y) = A(x,y) \exp\left[ i \frac{2\pi}{\lambda} W(x,y) \right]$$

- **点扩散函数 (PSF)：** 基于傅里叶光学，像面光场强度分布本质上是广义光瞳函数的傅里叶变换的模平方：

  $$PSF(u,v) = \left| \iint P(x,y) \exp\left[-i \frac{2\pi}{\lambda f}(ux+vy)\right] dx dy \right|^2$$

### **三、 像差的数学表征与多项式展开**

当 $W(x,y) \neq 0$ 时，点像退化为弥散斑。现代光学设计中，实际光程差（波像差）通常利用**泽尼克多项式 (Zernike Polynomials)** 在光瞳极坐标 $(\rho, \theta)$ 下进行正交展开：

$$W(\rho, \theta) = \sum_{j} C_j Z_j(\rho, \theta)$$

不同像差对应波前不同的形貌特征：

- **球差 (Spherical Aberration)：** 径向坐标的偶次函数（如 $W \propto \rho^4$），光线在不同孔径高度聚焦位置不同。
- **彗差 (Coma)：** 与坐标的奇次项相关（如 $W \propto \rho^3 \cos\theta$），引起非对称的彗星状弥散斑。
- **像散 (Astigmatism)：** 子午与弧矢方向曲率不同（如 $W \propto \rho^2 \cos^2\theta$）。
- **场曲 (Field Curvature)：** $W$ 随视场和孔径的平方变化，理想像面沿光轴弯曲，受系统佩茨瓦尔和 (Petzval Sum) 支配。
- **色差 (Chromatic Aberration)：** 介质色散导致 $\frac{\partial n}{\partial \lambda} \neq 0$，进而产生与波长相关的 $OPD(\lambda)$。

### **四、 成像质量的量化评估**

即使不存在几何像差（$OPD=0$），受限于系统孔径的衍射效应，点像依然是艾里斑（Airy Disk）。引入光程差后，中心能量会向高阶衍射环转移。

- **斯特列尔比 (Strehl Ratio, S.R.)：** 实际系统最大中心光强与理想衍射极限系统最大中心光强之比。其严格计算可由马哈詹近似 (Mahajan's Theorem) 给出：

  $$S.R. \approx \exp\left[ - \left( \frac{2\pi}{\lambda} OPD_{rms} \right)^2 \right]$$

  当像差较小（$OPD_{rms} < 0.1\lambda$）时，可泰勒展开退化为马瑞夏近似 (Maréchal Approximation)：

  $$S.R. \approx 1 - \left( \frac{2\pi}{\lambda} \right)^2 \left( OPD_{rms} \right)^2$$

  *(注：$OPD_{rms}$ 为全孔径内光程差的均方根值)*

- **瑞利判据 (Rayleigh Criterion)：** 当系统的最大波峰-波谷光程差 $|OPD_{PV}| \le \frac{\lambda}{4}$ 时，$S.R. > 0.8$，即可认为该系统成像质量良好，达到了**衍射极限 (Diffraction-limited)** 状态。



<!-- 下面内容必须整理后放进PPT中 -->
场曲矫正方法：正负光焦度分离、弯月透镜

像散：子午面和弧矢面的光束发散角存在差异，使得聚焦位置存在差异
像散矫正方法：采用改变光阑位置、非球面透镜方法

慧差为轴外球差，慧差矫正方法：可采用改变光阑位置、非球面透镜

球差：轴上光线与边缘光线和光轴焦点的轴向距离
球差矫正方法：分摊光焦度、透镜拆分（曲率半径较大时）、胶合透镜和非曲面透镜