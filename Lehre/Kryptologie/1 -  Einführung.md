>[!note] Was ist Kryptologie?
>**Kryptologie** ist ein Oberbegriff, welcher die **Theorie (Mathematik)** und **Praxis (Umsetzung)** rund um das Thema Verschlüsselung betrachtet. Kryptologie lässt sich dabei in zwei Hauptstränge unterteilen
>
>![[Figures/krypto_ubersicht.png|center|400]]
> Die oben genannten Oberbegriffe sind Disziplinen, die folgende Themen beinhalten
> - Krypographie:
> 	- Verschlüsselungsalgorithmen (häufig mithilfe von mathematisch ungelösten bzw. schwer lösbaren Problemen)
> 	- Erstellung von Signaturverfahren
> 	- Erstellung von kryptographischen Protokolen in Verbinung mit Verschlüsselungsalgorithmen 
> - Kryptoanalyse
> 	- analytische Auseinandersetzung mit kryptographischen Verfahren zum Zweck diese anzugreifen, das heißt unter anderem das ausgetauschte Geheimnis zu entschlüsseln oder auch Signaturen zu fälschen

>[!note] Klassifikation Kryptographischer Verschlüsselungsalgorithmen ([[../../PDFs/schneier1996.pdf#page=22|Quelle]])
>
>>[!algo]- Subsitutionsverfahren (Informativ)
>> In Substitutionsverfahren wird ein Zeichen einer Nachricht gegen ein (simpel) oder mehrere (homophonisch) Zeichen ausgetauscht. Einer der bekanntesten Vertreter ist die **Caesar Verschlüsselung**. Dabei nehmen wir ein Zeichen eines Alphabets und **verschieben es um 3 Stellen**. Die folgende Tabelle veranschaulicht die Verschlüsselung $\text{Caesar}(m_{i}) = c_{i}$ eines Klartextzeichens $m_i$
>>
>> ```
>> m_i:          a b c d e f g h i j k l m n o p q r s t u v w x y z
>> Caesar(m_i):  D E F G H I J K L M N O P Q R S T U V W X Y Z A B C
>> ```
>>
>> Es ist leicht zu sehen, dass es sich hierbei um eine **bijektive Abbildung** handelt, und somit die Entschlüsselung lediglich **die Umkehrfunktion** der Verschlüsselungsfunktion ist
>>
>>>[!remark]- Erinnerung Bijektive Abbildung
>>>Eine bijektive Abbildung ist eine Abbildung, die sowohl surjektiv als auch injektiv ist. 
>>>
>>><u>Injektivität:</u>
>>>Sei $f: U\to V$ eine Abbildung, die von der Menge $U$ zu der Menge $V$ abbildet. Die Abbildung $f$ heißt **injektiv**, wenn wir zwei beliebige $u_{1}, u_{2} \in U$ abbilden und deren Abbildung gleich ist, so müssen auch $u_{1}, u_{2}$ gleich sein. Die Definition ist gegeben als
>>>$$\forall u_{1}, u_{2} \in U: f(u_{1})= f(u_{2}) \implies u_{1}=u_{2}$$
>>>Wenn wir es uns grafisch veranschaulichen, können wir sinngemäß sagen, unsere Abbildung "schießt" jedes Element in der Zielmenge höchstens einmal ab.
>>>
>>>![[Figures/injektivität.png|center|550]]
>>>
>>><u>Surjektivität:</u>
>>> Sei $f: U\to V$ eine Abbildung, die von der Menge $U$ zu der Menge $V$ abbildet. Die Abbildung $f$ heißt **surjektiv**, wenn für jedes $v \in V$ ein passendes $u \in U$ gefunden werden kann, sodass $f(u)=v$ ist. Die Definition ist in kurz gegeben als
>>> $$\forall v \in V: \exists u \in U: f(u)=v$$
>>> ![[Figures/surjektivität.png|center|550]]
>>> 
>>> <u>Bijektivität</u>
>>> Sei $f: U\to V$ eine Abbildung, die von der Menge $U$ zu der Menge $V$ abbildet. Die Abbildung $f$ heißt **bijektiv**, wenn sie **injektiv** und **surjektiv** ist.
>>>
>>>![[Figures/bijektivität.png|center|180]]
>>>
>>>>[!remark] Bemerkung
>>>>Bijektivität garantiert uns, dass eine Umkehrfunktion (inverse Abbildung) $f^{-1}$ die Axiome des Abbildungsbegriffs erfüllt: 
>>>>- Ist eine Abbildung nicht surjektiv, so kann sie nicht jedes Argument in ihrer Umkehrung abbilden 
>>>>- Ist eine Abbildung nicht injektiv, so bildet ein Argument auf zwei verschiedene Werte in ihrer Umkehrung ab.
>>
>>Ein weiteres Beispiel ist der _ROT13_ Algorithmus, wo ähnlich zur Caesar Verschlüsselung um 13 statt 3 Stellen im Alphabet verschoben wird.
>>
>>>[!danger] Subsitutionsverschlüsselungen können leicht durch Frequenzanalyse von Zeichen gebrochen werden.
>>>
>
>>[!algo]- Transpositionsverfahren (Informativ)
>>Transpositionsverfahren schreiben eine Klartextnachricht Zeilenweise in einer fixen Spaltenlänge zunächst auf. Nehmen wir die Nachricht $$m =  \text{WIRLERNENKRYPTOLOGIE}$$
>>und setzen die Spaltenlänge $n=7$, so erhalten wir mit dem Padding Zeichen X
>>```
>>1 2 3 4 5 6 7
>>
>>W I R L E R N
>>E N K R Y P T
>>O L O G I E X
>>```
>>Ein Schlüssel gibt uns nun die Anweisung, wie wir die Spalten zu vertauschen haben. Wir nehmen den Schlüssel $p = \text{CGAFBDE}$. Somit erhalten wir für die Position im Alphabet des Schlüssels die Transpositionsanweisung
>>
>>```
>> C G A F B D E        Schlüssel in Buchstaben
>> 3 7 1 6 2 4 5        Schlüssel in Zahlen
>>
>>R N W R I L E
>>K T E P N R Y
>>O X O E L G I
>>```
>>Die Chiffre lautet demnach
>>$$c = \text{RNWRILEKTEPNRYOXOELGI}$$
>>
>>>[!danger] Transpositionsverfahren können mittels anderer Verfahren recht leicht gebrochen werden. (Siehe weiter unten)
>>
>>>[!example] Beispiel
>>>![[Figures/skytale.png|center|200]]
>>><center>Abbildung: Skytale - Antike Transpositionsverschlüsselung </center>
>>>Hier wird ein Lederband über einen Zylinder eines konkreten Durchmessers bespannt. Hierbei ist der Durchmesser des Zylinders der Schlüssel des Verfahrens. Ist das Lederband aufgespannt, so kann ein Text entlang des Zylinders auf das Lederband geschrieben werden. 
>>>
>>>Zieht man das Lederband ab, so hat man eine willkürlich anmutende Sammlung an Buchstaben. Nur der korrekte Durchmesser des Zylinders ermöglicht es das Lederband wieder korrekt aufzuziehen.
>>>
>
>>[!algo]- Rotationsmaschinen (Informativ)
>>Rotationsmaschinen sind nach dem ersten Weltkrieg in Erscheinung getreten und fanden ihre höchste Prominenz während des zweiten Weltkriegs mit dem wohl berühmtesten Vertreter der **Enigma**.
>>![[Figures/enigma.jpg|center| 400]]
>><center> Abbildung: Enigma mit Steckbrett unterhalb der Tastatur und  </center>
>><center> sichtbaren Rotoren oberhalb der Tastatur</center>
>>
>>Solche Maschinen bestehen aus mehreren Rotoren. Dabei entspricht jeder Rotor einer Permutation. Eine Permutation ist eine bijektive Abbildung $$\sigma: U \to U$$
>>![[Figures/rotor_wiring.jpg|center|400]]
>><center> Abbildung: Rotor mit Verdrahtung für Permutationseffekt </center>
>>
>>In der eben gezeigten Abbildung kann man sehen, wie von rechts ein Signal in Form eines Zeichens auf den Rotor trifft. Die Drähte sind beidseitig mit jeweils einer Kontaktscheibe verbunden (Eingang und Ausgang), wobei die Position vom Eingang zum Ausgang permutiert wird, genau gesagt unsere Permutation kann wie folgt ausgedrückt werden
>>$$\sigma(\text{Eingang}) = \text{Ausgang}$$
>>Was diese Art der Verschlüsselung von den Substitutionsverfahren unterscheidet ist, dass mehrere der Rotoren hintereinander geschaltet sind, und bei jeder Permutation sich (mindestens) einer der Rotoren dreht und somit die Permutation für die nächste Eingabe ändert. Dieser Mechanismus wurde in der Enigma mechanisch mit Hebeln gelöst
>>
>> ![[Figures/pawls.png|center|400]]
>> <center>Abbildung: Hebel bewegen Rotoren mit jedem Tastendruck </center>
>> 
>> Je nach Position der Rotoren, wird der Nachbarrotor auch bewegt. Dies ist ermöglicht durch Einlassungen, die im Rotorenring zu finden sind. Eine vollständige Beschreibung und Visualisierung dieses Mechanismus kann [hier (YouTube)](https://www.youtube.com/watch?v=ybkkiGtJmkM) gefunden werden.
>>
>>Durch eine rigorose mathematische Analyse und nachfolgend dem Einsatz von ersten maschinellen Verfahren konnte die Enigma durch die Polen und Alan Turing geknackt werden und somit einen entscheidenden Beitrag im Ausgang des zweiten Weltkriegs leisten.
>
>>[!algo]- Moderne Symmetrische Verschlüsselungsverfahren ([[../../PDFs/stallings1999.pdf#page=119|Quelle]]) (Informativ)
>>Die vorangegangenen Verfahren sind allesamt symmetrische Verschlüsselungsverfahren, welche in ihrer Anwendung folgende Charakteristik erfüllen
>>
>><center> Es wird derselbe Schlüssel für Ver- </center>
>><center> und Entschlüsselung verwendet </center>
>>
>>Allerdings gelten diese nach modernen Standards als unsicher, da diese mit modernen Computern leicht zu knacken sind. Moderne symmetrische Verfahren sind die **Stromverschlüsselungsverfahren** oder auch **Block Chiffren**. An dieser Stelle wird auf genauere Details verzichtet. Zwei prominente Verfahren dieser Klasse sind **DES** (Data Encryption Standard) und **AES** (Advanced Encryption Standard).
>
>>[!algo]- Asymmetrische Verschlüssungsverfahren ([[../../PDFs/stallings1999.pdf#page=285|Quelle]]) (Hauptthema)
>>Asymmetrische Verschlüsselungsverfahren haben die besondere Charakteristik, dass es nicht nur einen Schlüssel für Ver- und Entschlüsselung gibt, sondern ein Schlüsselpaar:
>> - $p_{k}$ - Öffentlicher Schlüssel (public key), welcher für jeden sichtbar ist und verwendet werden kann, um Nachrichten zu verschlüsseln.
>> - $s_{k}$ - Privater Schlüssel (secret/private key), welcher nur für den Erzeuger des Schlüsselpaars sichtbar ist. Nur mit diesem Schlüssel kann eine verschlüsselte Nachricht wieder zu eine Klartextnachricht entschlüsselt werden.
>> 
>> Diese Methode der Verschlüsselung ist eine junge und moderne Disziplin der Kryptologie. Sie trat erstmals 1977 mit dem **RSA** Algorithmus der Forscher Rivest, Shamri und Adleman auf.
>> 
>> Die Methoden der asymmetrische Verschlüsselung basieren auf entweder ungelösten (nur heuristisch (möglicherweise) lösbar) oder auch nur sehr schwer lösbaren Problemen. Dazu zählen:
>> - Faktorisierungsproblem von ganzen Zahlen
>> - Diskretes Logarithmus Problem
>> - Diskretes Logarithmusproblem auf Elliptischen Kurven
>> - Gitterbasierte diskrete Vektorprobleme
>
>>[!remark]- Bemerkung zu Frequenzanalyse ([[../../PDFs/stallings1999.pdf#page=96|Quelle]])
>> Wenn die Sprache einer Klartextnachricht bekannt ist und es sich bei dem Verschlüsselungsverfahren um eine einfache Permutation handelt, kann die Verteilung der Buchstaben analysiert werden und mit der bekannten Zielsprache verglichen werden. Somit ist es relativ einfach durch Zurücktauschen der Buchstaben anhand der Verteilung sich sukzessive dem Klartext anzunähern.
>> 
>> ![[Figures/frequenz_analyse.png|center|500]]
>> <center> Abbildung: Verteilung der Buchstaben in der englischen Sprache

>[!Theorem] Kerckhoffs' Prinzip
> Kerckhoffs' Prinzip besagt, dass die Sicherheit eines kryptologischen Verfahrens nicht von der Geheimhaltung des Verfahrens abhängig ist. Nach diesem Prinzip muss die Geheimhaltung des Schlüssels ausreichend sein.
>
>>[!remark] Bemerkung zu Folgerung aus Kerckhoffs' Prinizp
>>- es ist aufwändiger ein neues Verfahren zu entwickeln als einen neuen Schlüssel zu erzeugen
>>- wenn Algorithmen öffentlich zugänglich sind, können Fehler im Algorithmus durch andere Fachleute aufgezeigt werden
>
>>[!remark]- Bemerkung zu Kerckhoff und seinen Prinzipien
>>Auguste Kerckhoffs war ein niederländisch geborener, französischer Professor. Mit dem Aufkommen der telegraphischen Kommunikation hat 1883 Kerckhoff Prinzipien für das Militär formuliert, sodass für die Kommunikation sicherheitsrelevante Aspekte erfüllt. Dazu gehörte auch die Praktikabilität und Effizienz der Ver- und Entschlüsselung.


>[!terminology] Terminologie
>Die mathematische Symbolik wird nachgehend genauer eingeführt. Diese Sektion soll als Nachschlagewerk für die grundlegende Fachsprache dienen.
>
| Begriff                                                          | Bedeutung                                                                                                                                                                                                                          |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Klartextnachricht $m \in \mathbb{Z}_{n}$ <br>$m$ für **m**essage | die unverschlüsselte, für jedermann lesbare Nachricht                                                                                                                                                                              |
| Verschlüsselte Nachricht $c \in \mathbb{Z}_{n}$ <br>$c$ für **c**hiphre                 | die verschlüsselte Nachricht, die nur mittels eines Schlüssels in einen lesbare Klartextnachricht wieder überführt werden kann. Die Symbolik entspringt aus der englischen Sprache, wo der Begriff unter _Ciphertext_ bekannt ist. |
| Verschlüsselung $\text{Enc}(m)=c$                                | der Algorithmus, der aus einer Klartextnachricht eine verschlüsselte Nachricht erstellt.                                                                                                                                           |
| Entschlüsselung $\text{Dec}(c)=m$                                | der Algorithmus, der aus einer verschlüsselten Nachricht die originale Klartextnachricht mithilfe eines Schlüssels wieder herstellen kann                                                                                          |
| Kryptographischer Algorithmus (Cipher)                           | mathematische Funktion, welche für Ver- und Entschlüsselung verwendet wird. In der Regel gibt es jeweils eine Funktion für Ver- und Entschlüsselung.                                                                               |
| Kryptographisches Protokoll                                      | Anweisungsabfolge, der für zwei oder mehrere Teilnehmer den Zweck eines geheimen Austauschs von Informationen dient                                                                                                                |
| Angriff                                                          | der Versuch eine verborgene Informationen herzustellen oder auch Nachrichten zu fälschen                                                                                                                                           |
| Brute Force Angriff                                              | es wird versucht die Schlüsselraum durch systematisches Raten zu erschöpfen und eine semantisch plausible Nachricht zu finden                                                                                                      |
