---
theme: default
highlighter: shiki
transition: slide-left
layout: section
class: 'text-center'
lineNumbers: true
colorSchema: light
---

# 定理・補題・命題

---

## [**講義第一回**](https://syuntoku14.github.io/Foundations-of-RL-1)

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（マルコフ方策の最適性）**<sup>1</sup>：
任意の$\gamma \in [0, 1)$に対して，次が成り立つ．
$$
\max_{\pi \in \Pi^{\text{MSD}}} \operatorname{Ret}_\gamma(\pi) = \max_{\pi \in \Pi^{\text{MS}}} \operatorname{Ret}_\gamma(\pi) = \max_{\pi \in \Pi^{\text{H}}} \operatorname{Ret}_\gamma(\pi)
$$

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（マルコフ方策の最適性・有限ホライゾン）**<sup>2</sup>：
任意の$H < \infty$に対して，次が成り立つ．
$$
\max_{\pi \in \Pi^{\text{MS}}} \operatorname{Ret}_H(\pi) < \max_{\pi \in \Pi^{\text{MD}}} \operatorname{Ret}_H(\pi) = \max_{\pi \in \Pi^{\text{M}}} \operatorname{Ret}_H(\pi) = \max_{\pi \in \Pi^{\text{H}}} \operatorname{Ret}_H(\pi)
$$

</div>

<div style="font-size: 0.7em; text-align: left; position: absolute; bottom: 5px; left: 20px;">

[1] [強化学習（森村哲郎）](https://amzn.asia/d/7giaejg)の系1.2と命題2.7など\
[2] [Puterman+, 1994]の命題4.4.3**の応用

</div>

---

## [**講義第二回**](https://syuntoku14.github.io/Foundations-of-RL-2)

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（価値関数と逆行列）**：
任意の確率的マルコフ定常方策$\pi$と$\gamma \in [0, 1)$ に対して，次が成立する．
$$
V^\pi_\gamma = (I - \gamma P_\pi)^{-1} r_\pi
$$

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（ベルマン作用素の収束性）**：
$B_\pi^k$を，$B_\pi$を繰り返し$k$回適用した作用素とする．\
つまり，$B_\pi^k(v) = B_\pi(B_\pi(\cdots B_\pi(v))$とする．このとき，次の２つが成立する：
1. 任意の$v \in \mathbb{R}^{|\mathcal{S}|}$に対して，$V_\gamma^\pi = \lim_{k \to \infty} B_\pi^k(v)$
2. $B_\pi (v) = v$を満たす解 $v$は価値関数$V_\gamma^\pi$だけである．

</div>

---
hideInToc: true
---

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（ベルマン作用素の縮小性）**：
任意の$v, w \in \mathbb{R}^{|\mathcal{S}|}$に対して，次が成立する．

$$
\|B_\pi (v) - B_\pi (w)\|_\infty \leq \gamma \|v - w\|_\infty
$$

このように，$\|B (v) - B (w)\|_\infty \leq \gamma \|v - w\|_\infty$を満たす作用素$B$のことを**縮小作用素**と呼ぶ．

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**バナッハの不動点定理**：$B: \mathbb{R}^{|\mathcal{S}|} \to \mathbb{R}^{|\mathcal{S}|}$を，$\gamma \in [0, 1)$について次を満たすような縮小作用素とする．
$$
\|B(v) - B(w)\|_\infty \leq \gamma \|v - w\|_\infty  \quad \forall v, w \in \mathbb{R}^{|\mathcal{S}|}
$$

このとき，次の２つが成立する．
1. $B v^\star = v^\star$を満たすベクトル$v^\star \in \mathbb{R}^{|\mathcal{S}|}$が唯一存在する．
2. 任意の$v \in \mathbb{R}^{|\mathcal{S}|}$に対して，$\lim_{k \to \infty} B^k(v) = v^\star$が成立する．

証明：[バナッハの不動点定理のwiki](https://ja.wikipedia.org/wiki/%E3%83%90%E3%83%8A%E3%83%83%E3%83%8F%E3%81%AE%E4%B8%8D%E5%8B%95%E7%82%B9%E5%AE%9A%E7%90%86)参照．

</div>

---

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（ベルマン作用素の収束性）**：
$T_\pi^k$を，$T_\pi$を繰り返し$k$回適用した作用素とする．\
つまり，$T_\pi^k(q) = T_\pi(T_\pi(\cdots T_\pi(q))$とする．このとき，次の２つが成立する：
1. 任意の$q \in \mathbb{R}^{|\mathcal{S}\times \mathcal{A}|}$に対して，$Q_\gamma^\pi = \lim_{k \to \infty} T_\pi^k(q)$
2. $T_\pi (q) = q$を満たす解 $q$は価値関数$Q_\gamma^\pi$だけである．

</div>

---

## [**講義第三回**](https://syuntoku14.github.io/Foundations-of-RL-3)

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（任意の初期状態行動でのマルコフ方策の最適性）**<sup>1</sup>：

次を満たす$V^\star: \mathcal{S} \to \mathbb{R}$と$Q^\star: \mathcal{S} \times \mathcal{A} \to \mathbb{R}$を定義しよう．
$$
V^\star_\gamma(s) = \max_{\pi \in \Pi^{\text{H}}} V^\pi_\gamma(s), \quad Q^\star_\gamma(s, a) = \max_{\pi \in \Pi^{\text{H}}} Q^\pi_\gamma(s, a)
$$

この$V^\star_\gamma$と$Q^\star_\gamma$を，それぞれ**最適状態価値関数**と**最適行動価値関数**と呼ぶ．

このとき，次を満たす決定的なマルコフ定常方策$\pi^\star \in \Pi^{\text{MSD}}$が存在する．

$$
V^{\pi^\star}_\gamma(s) = V^\star_\gamma(s), \quad Q^{\pi^\star}_\gamma(s, a) = Q^\star_\gamma(s, a) \quad \forall s \in \mathcal{S}, a \in \mathcal{A}
$$

</div>

<div style="font-size: 0.7em; text-align: left; position: absolute; bottom: 5px; left: 20px;">

[1] [Reinforcement Learning: Theory and Algorithms](https://rltheorybook.github.io/)の定理1.7など

</div>



---
hideInToc: true
---

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**補題（状態行動訪問確率とマルコフ方策の十分性）**<sup>1</sup>：

任意の履歴依存方策$\pi^{\text{H}} \in \Pi^{\text{H}}$に対して，次を満たす確率的マルコフ非定常方策$\pi^{\text{M}} \in \Pi^{\text{M}}$が存在する

$$
\mathbb{P}^{\pi^{\text{H}}}_\mu(s_h = s, a_h = a) = \mathbb{P}^{\pi^{\text{M}}}_\mu(s_h = s, a_h = a) \quad \forall (h, s, a) \in \mathbb{N} \times \mathcal{S} \times \mathcal{A} 
\tag{1}
$$

$\mathbb{P}^\pi_\mu(s_h=s, a_h=a)$は，$\pi$が時刻$h$で$s, a$を訪問する確率を表す．

</div>

<div style="font-size: 0.7em; text-align: left; position: absolute; bottom: 5px; left: 20px;">

[1] [強化学習（森村哲郎）](https://amzn.asia/d/7giaejg)の命題1.1など

</div>




---



<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（最適ベルマン作用素の縮小性）**：
任意の$v, w \in \mathbb{R}^{|\mathcal{S}|}$に対して，次が成立する．

$$
\|B_\star (v) - B_\star (w)\|_\infty \leq \gamma \|v - w\|_\infty
$$

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（最適ベルマン作用素の収束性）**：
$B_\star^k$を，$B_\star$を繰り返し$k$回適用した作用素とする．\
つまり，$B_\star^k(v) = B_\star(B_\star(\cdots B_\star(v))$とする．このとき，次の２つが成立する：
1. 任意の$v \in \mathbb{R}^{|\mathcal{S}|}$に対して，$V_\gamma^\star = \lim_{k \to \infty} B_\star^k(v)$
2. $B_\star (v) = v$を満たす解 $v$は価値関数$V_\gamma^\star$だけである．

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（ベルマン作用素の変化と価値の誤差）**：
$v \in \mathbb{R}^{|\mathcal{S}|}$が$\|B_\star (v) - v\|_\infty \leq \varepsilon$ならば，次が成立する
$$
\|B_\star(v) - V^\star_\gamma\|_\infty \leq \frac{\gamma \varepsilon}{1-\gamma}
$$

</div>

---
hideInToc: true
---

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（$V^\star$と$Q^\star$の関係）**： $V^\star_\gamma(s) = \max_{a \in \mathcal{A}} Q^\star_\gamma(s, a)$が任意の$s \in \mathcal{S}$で成り立つ．

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**補題（ベルマン作用素の単調性）**： 関数$v, w \in \mathbb{R}^{|\mathcal{S}|}$が $v(s) \leq w(s)$を全ての$s \in \mathcal{S}$で満たすとき，

$$
B^k_\star(v)(s) \leq B^k_\star(w)(s) \quad \forall s \in \mathcal{S}, k \in \mathbb{N}
$$

が成り立つ．ちなみに$B_\pi$も同様の性質を持つ（証明は省略する）．

このように，$v \leq w$ならば$B(v) \leq B(w)$を満たす関数$B$は**単調性がある**と言う<sup>1</sup>．

</div>

<br>

---

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**縮小性補題：** $B: \mathbb{R}^{|\mathcal{S}|} \to \mathbb{R}^{|\mathcal{S}|}$を単調な縮小作用素とする．
$v^\star$を$B$の不動点とする．\
また，$g: \mathbb{R}^{|\mathcal{S}|} \to \mathbb{R}$を，$v \geq w$ならば$g(v) \geq g(w)$を満たすような非減少な関数とする．\
このとき，次が成立する．
$$
g(v^\star) = \min\{g(v) \rvert v \geq B(v)\} = \max\{g(v) \rvert v \leq B(v)\} \tag{1}
$$

さらに$g$が，$v > w$ならば$g(v) > g(w)$を満たすような単調増加な関数のとき，$v^\star$は式(1)を満たす唯一の解になる．

</div>

<br>

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**補題（拡張占有率と方策）：** 初期状態分布が$\mu > \boldsymbol{0}$を満たすとする．
任意のマルコフ定常方策$\pi, \pi' \in \Pi$ が $\pi = \pi'$ であるとき，かつそのときに限り，
互いの拡張占有率は$\omega^{\pi}_\mu = \omega^{\pi'}_\mu$を満たす．

</div>

---

<div style="border: 2px solid #000; padding-top: 1px; padding-left: 10px; margin-top: 5px; background-color: rgb(220, 241, 255);">

**命題（双対問題と占有率<sup>1</sup>）：** $\omega \in \mathbb{R}^{|\mathcal{S}\times\mathcal{A}|}$が $\omega \geq \boldsymbol{0}$ かつ $(\widetilde{I} - \gamma P)^\top \omega = \mu$を満たす時，$\omega$による方策

$$
\widetilde{\pi}(a \rvert s) = \frac{\omega(s, a)}{\sum_{a' \in \mathcal{A}} \omega(s, a')} \quad \forall s, a \in \mathcal{S}\times \mathcal{A}
$$

の拡張占有率$\omega^{\widetilde{\pi}}_\mu$は$\omega$と一致する．つまり，$\omega = \omega^{\widetilde{\pi}}_\mu$が成り立つ．

</div>

---

## [**講義第四回**](https://syuntoku14.github.io/Foundations-of-RL-4)

