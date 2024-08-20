>[!remark] Bemerkung: Motivation zum Kapitel
>Im Kapitel [[2 - Algebraische und Zahlentheoretische Grundlagen (1)]] haben wir grundlegende algebraische Strukturen eingeführt. Wir erinnern uns, dass wir [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppen und kommutative Gruppen]] kennen, die je nachdem die Eigenschaften
>1. Assoziativität
>2. Existenz des neutralen Elements
>3. Existenz der inversen Elemente
>4. Kommutativität
>
>bestehen. Die Forderung dieser Eigenschaften hat es uns ermöglicht eine Struktur aufzubauen, die mit Hilfe von zahlentheoretischen Eigenschaften in kryptologischen Verfahren mündete. Wir vertiefen nun Konzepte der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)|algebraischen Strukturen]], um damit neue kryptologische Verfahren zu beschreiben.

>[!def] Definition Untergruppe ([[../../PDFs/judson2022.pdf#page=50|Quelle]])
>Sei $(G, \circ)$ eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]], dann ist $H \subseteq G$ mit $(H, \circ)$ eine Untergruppe, wenn
>$$\forall h_{1},h_{2} \in H: h_{1}$$
>
>>[!example] Beispiel
>>Sei $G=(\mathbb{Z},+)$, dann ist $(2\mathbb{Z},+)$ eine Untergruppe bezüglich $G$ mit $2\mathbb{Z}=\{ \dots,-4,-2,0,2,4,\dots \}$, weil