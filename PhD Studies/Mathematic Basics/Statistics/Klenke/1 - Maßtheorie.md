>[!def] Definition Eigenschaften von Mengensystemen
> Sei $\Omega \neq \emptyset$ und $\mathcal{A} \subset 2^{\Omega}$
>1. $\cap$-stabil (schnittstabil):  $$A,B \in \mathcal{A}:A \cap B \in \mathcal{A}$$
>2. $\sigma-\cap$-stabil (sigma-schnittstabil): <br> Für je abzählbar unendlich viele Mengen gilt $$A_{1},A_{2},\dots \in \mathcal{A}: \bigcap_{n=1}^\infty A_{n} \in \mathcal{A}$$
>3. $\cup$-stabil (vereinigungsstabil):  $$A,B \in \mathcal{A}: A \cup B \in \mathcal{A}$$
>4. $\sigma-\cup-stabil$ (sigma-vereinigungsstabil): <br> Für je abzählbar unendlich viele Mengen gilt $$A_{1},A_{2},\dots \in \mathcal{A}: \bigcup_{n=1}^\infty A_{n} \in \mathcal{A}$$
>5. $\setminus$-stabil (differenzmengenstabil): $$A,B \in \mathcal{A}: A \setminus B \in \mathcal{A}$$
>6. komplementstabil: $$A \in \mathcal{A} \implies A^c := (\Omega\setminus A) \in \mathcal{A}$$

^5e97de

>[!def] Definition Mengensysteme
> Sei $\Omega \neq \emptyset$ und $\mathcal{A} \subset 2^{\Omega}$
>
> ---
>>$\sigma$-Algebra
>> 1. $\Omega \in \mathcal{A}$
>> 2. $\mathcal{A}$ ist *komplementstabil*
>> 3. $\mathcal{A}$ ist $\sigma-\cup-$*stabil*
> 
> ---
>
>> Algebra
>> 1. $\Omega \in \mathcal{A}$
>> 2. $\mathcal{A}$ ist $\setminus$-*stabil*
>> 3. $\mathcal{A}$ ist $\cup$-*stabil*
> ---
>> Ring / $\sigma$-Ring
>> 1. $\emptyset \in \mathcal{A}$
>> 2. $\mathcal{A}$ ist $\setminus$-*stabil*
>> 3. $\mathcal{A}$ ist $\cup$-*stabil*
>>
>> Ein Ring heißt $\sigma$-Ring, falls er $\sigma$-$\cup$-stabil ist.
>---
>> Semiring/Halbring
>> 1. $\emptyset \in \mathcal{A}$
>> 2. $\forall A,B \in \mathcal{A}: \exists A_{1},A_{2},\dots,A_{n} \in \mathcal{A}: \biguplus_{i=1}^nA_{i}=B \setminus A$
>> 3. $\mathcal{A}$ ist $\cap$-*stabil*
>>
>> $\biguplus$ steht für die disjunkte Vereinigung
>---
>> Dynkin-System / $\lambda$-System
>> 1. $\Omega \in \mathcal{A}$
>> 2. $\forall A,B \in \mathcal{A}, A \subset B: (B \setminus A) \in \mathcal{A}$
>> 3. Für je abzählbar viele, paarweise disjunkte Mengen $A_{1}, A_{2}, \dots \in \mathcal{A}$ gilt $$\biguplus_{n=1}^\infty A_{n}\in \mathcal{A}$$
>
><center> Zusammenhang der Mengensysteme </center>
>
>![[../../../../Pasted image 20250419214005.png|center|600]]

^017c60


>[!theorem] Satz Schnitt von Mengensystemen.
> Ist $I$ eine beliebige Indexmenge und $A_{i}$ eine $\sigma$-Algebra für jedes $i \in I$, so ist
> $$\mathcal{A}_{I} := \{ A \subset \Omega : A \in \mathcal{A}_{i}, i \in I \} = \bigcap_{i \in I} A_{i}$$
> eine $\sigma$-Algebra. Dies gilt analog für
> - Ringe
> - $\sigma$-Ringe
> - Algebren
> - Dynkin-Systeme
> 
>>[!remark]- Bemerkung: Dies gilt nicht für Semiringe
>>Seien 
>> - $\Sigma=\{ 1,2,3,4 \}$ 
>> - $\mathcal{A}_{1} = \{ \emptyset, \Omega, \{ 1 \}, \{ 2,3 \}, \{ 4 \} \}$ 
>> - $\mathcal{A}_{2} =\{ \emptyset, \Omega, \{ 1 \}, \{ 2 \}, \{ 3, 4 \} \}$
>>
>>Wir sehen, dass $\mathcal{A}_{1}, \mathcal{A}_{2}$ [[#^017c60|Semiringe]] sind. Allerdings ist
>>$$\mathcal{A}_{1} \cap \mathcal{A}_{2} = \{ \emptyset, \Omega, \{ 1 \} \}$$
>>keiner.
>
>>[!proof]- Beweis
>> Wir zeigen, dass die Bedingungen der $\sigma$-Algebra erfüllt sind aus der obigen [[#^017c60| Definition]].
>> 1. Da jedes $\mathcal{A}_{i}$ eine $\sigma$-Algebra ist, so muss auch gelten $\Omega \in \mathcal{A}_{i}$. Da wir über alle $\mathcal{A}_{i}$ schneiden, ist zwangsläufig $\Omega \in \mathcal{A}_{I}$. $$\tag*{$\checkmark$}$$
>> 2. Angenommen $A \in \mathcal{A}_{I}$, dann ist auch $A \in \mathcal{A}_{i}$ für alle $i \in I$. Wiederum muss demnach auch $A^c \in \mathcal{A}_{i}$ für alle $i \in I$, daher ist auch $A^c \in \mathcal{A}_{I}$. Somit ist $\mathcal{A}_{I}$ schnittstabil. $$\tag*{$\checkmark$}$$
>> 3. Seien $A_{1}, A_{2},\dots \in \mathcal{A}_{I}$. Dann ist $A_{n} \in \mathcal{A}_{i}$ für alle $n \in \mathbb{N}$ und $i \in I$. Da $\mathcal{A}_{i}$ $\sigma$-vereinigungsstabil ist, ist demnach auch $A = \bigcup_{n=1}^\infty A_{n} \in \mathcal{A}_{i}$ für alle $i \in I$. Demnach muss auch $A \in \mathcal{A}_{I}$ sein. $$\tag*{$\checkmark$}$$
>> $$\tag*{$\square$}$$

^6998ca

>[!theorem] Satz Erzeugte $\sigma$-Algebra
Sei $\mathcal{E} \subset 2^{\Omega}$. Dann existiert eine kleinste $\sigma$-Algebra $\sigma(\mathcal{E})$ mit $\mathcal{E} \subset \sigma(\mathcal{E})$:
$$\sigma(\mathcal{E}): = \bigcap_{\substack{\mathcal{A} \subset 2^{\Omega} \text{ ist } \sigma \text{-Algebra} \\ \mathcal{A} \supset \mathcal{E}}} \mathcal{A}$$
$\sigma(\mathcal{E})$ heißt die von $\mathcal{E}$ **<span style="color:#38ffa9">erzeugte <span class="math">\sigma</span>-Algebra</span>**. $\mathcal{E}$ heißt **<span style="color:#38ffa9">Erzeuger</span>** von $\sigma(\mathcal{E})$. Analog wird das von $\mathcal{E}$ erzeugte Dynkin-System $\delta(\mathcal{E})$ definiert.
>>[!proof]- Beweis
>>Dass $\sigma(\mathcal{E})$ eine $\sigma$-Algebra ist folgt aus dem [[#^6998ca| Satz des Schnittes von Mengensystemen]]. Da wir über alle $\sigma$-Algebren, die $\mathcal{E}$ enthalten, einen Schnitt bilden, muss es demnach auch die kleinste $\sigma$-Algebra sein, die $\mathcal{E}$ enthält.


>[!def] Definition Topologie
>Sei $\Omega \neq \emptyset$ eine beliebige Menge. Ein Mengensystem $\tau \subset 2^{\Omega}$ heißt **<span style="color:#38ffa9">Topologie</span>** auf $\Omega$, falls folgende drei Eigenschaften gelten.
>1. $\emptyset, \Omega \in \tau$
>2. $A,B \in \tau \implies A \cap B \in \tau$
>3. Sei $\mathcal{F} \subset \tau$ eine beliebige Familie, so ist auch $\left( \bigcup_{\mathcal{A}\in\mathcal{F}} A\right)\in \tau$
>
>Das Paar $(\Omega, \tau)$ heißt dann **<span style="color:#38ffa9">topologischer Raum</span>**. Die Mengen $A \in \tau$ heißen **<span style="color:#38ffa9">offen</span>**. Die Mengen $A \subset \Omega$ mit $A^c \in \Omega$ heißen **<span style="color:#38ffa9">abgeschlossen</span>**.
>>[!remark] Bemerkung: Typische Topologien
>>Sei $d$ eine Metrik auf $\Omega$
>>$$B_{r}(x) = \{ y \in \Omega: d(x,y) < r \} \tag{offene Kugel mit $r > 0$}$$
>>So ist eine Topologie
>>$$\tau=\left\{  \bigcup_{(x,r) \in \mathcal{F}} B_{r}(x) \;\;\Bigg\vert\;\; F \subset \Omega \times (0,\infty)  \right\}$$


>[!def] Definition Borel'sche $\sigma$-Algebra
>Sei $(\Omega, \tau)$ ein topologischer Raum. Die von den offenen Mengen erzeugte $\sigma$-Algebra
>$$\mathcal{B}(\Omega):= \mathcal{B}(\Omega, \tau):= \sigma(\tau)$$
>heißt **<span style="color:#38ffa9">Borel'sche $\sigma$-Algebra</span>** auf $\Omega$. Die Elemente $A \in \mathcal{B}(\Omega, \tau)$ heißen **<span style="color:#38ffa9">Borel'sche Mengen</span>** oder **<span style="color:#38ffa9">Borel-messbare Mengen</span>**.
