---
theme: default
highlighter: shiki
transition: slide-left
layout: section
class: 'text-center'
lineNumbers: true
colorSchema: light
---

# 用語・表記

---
layout: two-cols
---

<div style="font-size: 0.7em;">

**一般の数学表記**

* 実数空間：$\mathbb{R}$
* 自然数の集合（0を含まない）：$\mathbb{N}$
* 集合$\mathcal{S}$上の確率分布の集合：$\Delta(\mathcal{S})$
* $f: \mathcal{X} \to \mathcal{Y}$は集合$\mathcal{X}$から集合$\mathcal{Y}$への写像（関数）
* $a \triangleq b$は$a$を$b$で定義することを表す
* $x \in \mathbb{R}^d$に対して，$\|x\|_\infty = \max_{1 \leq i \leq d} |x_i|$は∞ノルム（最大値ノルム）
* $\|x\|_2 = \sqrt{\sum_{i=1}^d |x_i|^2}$は2ノルム（ユークリッドノルム）
* $v, w \in \mathbb{R}^d$に対して，$v \leq w$は$v_i \leq w_i$を全ての$i$で満たすことを表す
* $v < w$は$v\leq w$ かつ $v_i < w_i$を満たす$i$が存在することを表す
* $x, y \in \mathbb{R}^d$について，$x \propto y$は$x = c y$を満たすスカラー$c > 0$が存在することを意味する．
* $v \in \mathbb{R}^d$と$b \in \mathbb{R}$に対して，$v + b$は$b$を$v$の各成分に加えたベクトル
* $\boldsymbol{0} = (0, 0, \ldots, 0) \in \mathbb{R}^d$は要素が全て0のベクトル
* $\boldsymbol{1} = (1, 1, \ldots, 1) \in \mathbb{R}^d$は要素が全て1のベクトル

</div>

::right::

<div style="font-size: 0.7em;">

**MDPの表記**

* MDPの定義：$(\mathcal{S}, \mathcal{A}, P, r, \mu)$
  * 状態集合：$\mathcal{S}$
  * 行動集合：$\mathcal{A}$
  * 遷移確率関数：$P: \mathcal{S} \times \mathcal{A} \to \Delta(\mathcal{S})$
  * 報酬関数：$r: \mathcal{S} \times \mathcal{A} \to \mathbb{R}$
  * 初期状態分布：$\mu \in \Delta(\mathcal{S})$
* ホライゾン：$H \in \mathbb{N}$
* 割引率：$\gamma \in [0, 1)$
* エフェクティブホライゾン：$H_{\gamma, \varepsilon} \triangleq \frac{\ln \left(\frac{1}{\varepsilon(1-\gamma)}\right)}{\ln (1 / \gamma)}$\
（単に$1/(1-\gamma)$をエフェクティブホライゾンと言うことも多い）．

</div>

---
layout: two-cols
---

<div style="font-size: 0.7em;">

**方策などの表記**

* 方策の集合の種類：
  * 決定的マルコフ定常方策：$\Pi^{\text{MSD}}$
  * 確率的マルコフ定常方策：$\Pi^{\text{MS}}$
    * 特に断りがない限り，$\Pi$は$\Pi^{\text{MS}}$を表す．
  * 決定的マルコフ非定常方策：$\Pi^{\text{MD}}$
  * 確率的マルコフ非定常方策：$\Pi^{\text{M}}$
  * 決定的履歴依存方策：$\Pi^{\text{HD}}$
  * 確率的履歴依存方策：$\Pi^{\text{H}}$
* 方策：$\pi \in \Pi$
* 時刻$t$までにありえる履歴の集合：$\mathcal{H}_t=(\mathcal{S}\times \mathcal{A})^t$
* 有限ホライゾン期待収益関数：$\operatorname{Ret}_H: \Pi \to \mathbb{R}$
* 割引期待収益関数：$\operatorname{Ret}_\gamma: \Pi \to \mathbb{R}$
* 期待値の略記：$\mathbb{E}^\pi_\mu\left[\cdots\right] = \mathbb{E}\left[\cdots \rvert s_h, a_h \sim \pi, s_1 \sim \mu\right]$
    * 初期状態分布$\mu$に依存しない場合は$\mathbb{E}^\pi[\cdots]$を使う．
* $\pi$が時刻$h$で$s, a$を訪問する確率： $\mathbb{P}^\pi_\mu(s_h=s, a_h=a)$
* 一様方策：全ての行動を等確率$\frac{1}{|\mathcal{A}|}$で選ぶ方策．
* 貪欲方策：与えられた$Q$関数$q: \mathcal{S}\times \mathcal{A} \to \mathbb{R}$に対して，「各状態$s$で$\arg\max_a q(s, a)$を選択する方策」

</div>

::right::

<div style="font-size: 0.7em;">

**ベルマン方程式・作用素など**

* 方策$\pi$の状態価値関数：$V^\pi_\gamma: \mathcal{S} \to \mathbb{R}$
    * 方策で正規化した報酬関数：$r_\pi(s)=\sum_{a \in \mathcal{A}} \pi(a \rvert s) r(s, a)$
    * 方策で正規化した繊維関数：$P_\pi\left(s^{\prime} \rvert s\right)=\sum_{a \in \mathcal{A}} \pi(a \rvert s) P\left(s^{\prime} \rvert s, a\right)$
    * ベルマン方程式：$V^\pi_\gamma = r_\pi + \gamma P_\pi V^\pi_\gamma$
    * ベルマン作用素：$B_\pi(v) \triangleq r_\pi + \gamma P_\pi v$
* 占有率：$d^\pi_\mu = \mu^{\top}\left(I-\gamma P_\pi\right)^{-1}$
* 拡張占有率：$\omega^\pi_\mu(s, a) = \pi(a \rvert s) d^\pi_\mu(s)$
* 方策$\pi$の行動価値関数：$Q^\pi_\gamma: \mathcal{S} \times \mathcal{A} \to \mathbb{R}$
    * 方策をかけた遷移関数：$\bar{P}_\pi\left(s^{\prime}, a^{\prime} \rvert s, a\right)=\pi\left(a^{\prime} \rvert s^{\prime}\right) P\left(s^{\prime} \rvert s, a\right)$
    * 行動価値関数のベルマン方程式：$Q_\gamma^\pi=r+\gamma \bar{P}_\pi Q_\gamma^\pi$
    * 行動価値関数のベルマン作用素：$T_\pi(q) \triangleq r+\gamma \bar{P}_\pi q$

</div>

---
layout: two-cols
---

<div style="font-size: 0.7em;">

**最適ベルマン方程式・作用素など**

* 最適状態価値関数：$V^\star_\gamma: \mathcal{S} \to \mathbb{R}$
    * 最適ベルマン方程式：$\forall s \in \mathcal{S}$で，\
    $V^\star_\gamma(s) = \max_{a \in \mathcal{A}}\left(r(s, a) + \gamma \sum_{s' \in \mathcal{S}} P(s' \rvert s, a) V^\star_\gamma(s')\right)$
    * 最適ベルマン作用素：$\forall s \in \mathcal{S}$で，\
    $(B_\star (v))(s) \triangleq \max_{a\in \mathcal{A}} \left( r(s, a) + \gamma \sum_{s' \in \mathcal{S} }P(s' \rvert s, a) v(s')\right)$
* 最適行動価値関数：$Q^\star_\gamma: \mathcal{S} \times \mathcal{A} \to \mathbb{R}$
    * 行動価値関数のベルマン方程式：$\forall s, a \in \mathcal{S}\times \mathcal{A}$で，\
    $Q^\star_\gamma(s, a) = r(s, a) + \gamma \sum_{s' \in \mathcal{S}} P(s' \rvert s, a) \max_{a' \in \mathcal{A}} Q^\star_\gamma(s', a')$
    * 行動価値関数のベルマン作用素：$\forall s, a \in \mathcal{S}\times \mathcal{A}$で，\
    $(T_\star(q))(s, a) \triangleq r(s, a) + \gamma \sum_{s' \in \mathcal{S}} P(s' \rvert s, a) \max_{a' \in \mathcal{A}} q(s', a')$

</div>
