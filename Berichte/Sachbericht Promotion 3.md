# Übersicht der erarbeiteten Inhalte

Im ersten Jahr des Projekts wurde überwiegend Fundamentalwissen zum Thema Differenzialgleichungen erarbeitet, um mögliche prototypbasierte Klassifikatoren für Zeitreihen zu entwickeln. Diese sollen es ermöglichen interpretierbare Modelle aus dem euklidischen Raum auf heterogene Datenräume zu erweitern, um prototypbasierte Modelle in ihrem Anwendungsfeld zu erweitern.

Die Kontakte zu Forschern in Groningen (Niederlande), welche ebenfalls an Differenzialgleichungssystemen und dynamischen System forschen, haben interessante und vielversprechende Gespräche ergeben. Das sehr tiefgehende Expertenwissen hat mögliche Probleme und auf anderer Seite wiederum mögliche Potenziale des vorgelegten Grunddesigns ergeben, weshalb weitere Forschung in dem Feld potenziell die Lösung für einen noch unbekannten jedoch erstrebenswerten Ansatz der Darstellung von prototypbasierten Modellen aufzeigt.

Im Zuge der Zusammenarbeit mit den PhD Studenten in Mittweida, konnten wir ein weiteres Feld erschließen, welches im Bereich der Daten in komplexen Datenstrukturen wiederzufinden ist. Herr Ronny Schubert hat im Zusammenhang im Bereich des maschinellen Lernens in verteilten Systemen (Federated Learning) die Wiederherstellung von Daten über den Austausch von Gradienten in prototypbasierten Netzwerken untersucht und darin festgestellt, dass nicht nur in den generell bekannten Feedforward/Deep Neuronalen Netzwerken die Daten über die Gradienten hergestellt werden können, sondern ebenfalls (oder auch vor allem) in prototypbasierten Netzwerken. Gute Kenntnisse in Kryptologie haben die Idee hervorgebracht, die prototypbasierten Netzwerke in Vollhomorphen Verschlüsselungsverfahren umzusetzen. Das heißt, man verschlüsselt die Daten und die Modellparameter und berechnet vollhomomorph im Schlüsselraum das Modell.

Diese Herangehensweise, maschinelle Lernmodelle verschlüsselt zu lernen, liefert vielversprechende Lösungen für höchst schwierige Situationen. Angenommen man hat ein Lernproblem im medizinischen Sektor und Daten verteilt über verschiedene Akteure wie beispielsweise Krankenhäuser. Ein offensichtliches Problem ist, dass medizinische Daten hochsensible Informationen enthalten und außerdem durch die Datenschutzgrundverordnung geschützt sind. Es gibt bereits verschiedene Ansätze, wie beispielsweise im Differential Learning, wo bereits Versuche unternommen werden diesen Ansprüchen gerecht zu werden. Jedoch ist eine vollständige Verschlüsselung die wohl sichereste Variante Daten vor fremden Zugriffen zu schützen. Zumal nicht nur die Daten, sondern sogar vollständig das gesamte Modell vollständig verschlüsselt ist und vor Zugriff dritter geschützt wird. 

Unter diesem Aspekt wurde ein Paper geschrieben, welches ein prototypbasiertes Netzwerk (LVQ1) mit dem Verfahren "Fully Homomorphic Encryption over the Torus" (TFHE) umsetzte. Dabei wurde wie oben beschrieben ein Datensatz und die Modellparameter vollständig verschlüsselt und im Schlüsselraum trainiert. Dabei traten interessante Effekte auf. Zunächst wurde ein Verschlüsselungsverfahren verwendet welches hauptsächlich auf Ganzzahlen arbeitet, aber jedoch maschinelles Lernen für gewöhnlich mit reellen/rationalen Zahlen arbeitet. Dies hat der Leistung des Netzwerkes jedoch keinen Abbruch getan. Vielmehr hat auch die Art des Verschlüsselungsverfahren uns gezwungen die Tiefe der Datenrepräsentation stark einzukürzen, sodass es nur stark begrenzt viele Ganzzahlen gab, womit man die Datenvektoren ausdrücken konnte. Auch hier konnte beobachtet werden, dass es das Lernproblem nicht beeinträchtigt hat, und sogar minimal bessere Leistungen zeigte. Eine weitere wichtige Erkenntnis ist, dass vollhomomorphe Verschlüsselungsverfahren eine äußerst hohe Komplexität aufweisen, sodass es enorm wichtig ist ein geeignetes Verfahren für diese Methode zu wählen. Für die meisten Forscher ist die konventionelle Go-To Methode für maschinelles Lernen die klassischen Feedforward-Netzwerke. Analysen haben gezeigt, dass diese für vollhomomorphe Verschlüsselungsverfahren große Nachteile haben gegenüber prototypbasierten Netzwerken. Prototypbasierte Netzwerke können ohne spezielle Aktivierungsfunktionen auskommen, da die Nichtlinearität durch den Einsatz mehrerer Prototypen realisiert werden kann. Jedoch verwenden Feedforward-Netzwerke in jedem einzelnen Neuron nicht-lineare Aktivierungsfunktionen, die sehr teuer im Schlüsselraum approximiert werden müssen, weshalb ein Training von Klassifikatoren oder anderen Modellen vollhomomorph kaum bis gar nicht realisierbar sind. Das Paper wurde zur ESANN 2025 eingereicht.

Die zuletzt genannten Aspekte haben Anlass dazu gegeben, weitere Untersuchungen in diesem Feld zu unternehmen. 
1. Untersuchung welche weiteren homomorphen Verschlüsselungsverfahren für diese Zwecke geeignet sind
2. Untersuchung inwiefern ganzzahlige Repräsentationen für Lernverfahren geeignet sind
3. Untersuchung inwieweit Daten in ihrer Repräsentationstiefe minimiert werden können

Letzterer Punkt ist insofern von Interesse, da eine entsprechende Aussage zu einer Aussage der Parameterwahl in vollhomomorphen Verschlüsselungsverfahren führen kann.

# Aussage zur Zeitplanung

Trotzdessen, dass gerade ein thematischer Einschub erfolgt ist, ist der Zeitplan in einem guten Status. Gerade das Thema zu vollhomomorpher Verschlüsselung in Verbindung mit prototypbasierten Netzwerken ist ein nahezu unberührtes Gebiet. Dieses Gebiet ermöglicht eine Vielzahl von äußerst vielversprechenden Anwendungen, wie beispielsweise das Lernen in verteilten System auf hochsensiblen Daten. Es ist zu beobachten, dass gerade im medizinischen Bereich Lernprobleme nur schwer umsetzbar sind unter den regulatorischen und ethischen Auflagen. Fortschritte in diesem Bereich sind nicht nur für das Projektvorhaben, sondern auch gesellschaftlich und auch wirtschaftlich von großem Interesse.

Der angepasste Zeitplan sieht vor, mehr Arbeit in die Fundamentalkenntnisse zu den Themen aus der oben genannten Liste durchzuführen, sodass fundamentale Arbeit dazu durchgeführt werden kann. Deshalb sehen die nachfolgenden Schritte wie folgt aus.

1. Besuchen eine Konferenz, welche sich mit dem Thema vollhomomorpher Verschlüsselung beschäftigt.
2. Netzwerken mit Forschern im Bereich vollhomomorpher Verschlüsselung, um gemeinsam Fortschritte mit maschinellem Lernen zu erreichen
3. Fundamentalkenntnisse zu den Prinzipien und der Mathematik im Bereich vollhomomorpher Verschlüsselung erarbeiten.
4. Entwurf einer Arbeit, um das Lernverhalten von prototypbasierten Verfahren in eingeschränkten Datenrepräsentationen zu untersuchen

Das Thema zu Zeitreihendaten und prototypbasierten Netzwerken wird vorläufig aufgeschoben, da gerade im Bereich der vollhomomorphen Verschlüsselungsverfahren Ergebnisse schnell produzierbar sind.

# Weiterführende Bildung

Im Oktober 2024 wurde die ESANN 2024 in Brügge besucht, um sich ein Bild der aktuellen Forschung im Bereich maschinellem Lernen zu verschaffen und zu netzwerken. Dabei konnten Kontakte vor allem mit den Forschern aus Groningen vertieft werden, die Interesse an den Ideen zu den Zeitreihendaten und prototypbasierten Netzwerken zeigen.

Außerdem wurde im Zusammenhang mit den Arbeiten rund um die vollhomomorphen Verschlüsselungsverfahren die Lehrveranstaltung "Grundlagen und Anwendungen der Kryptologie" vollständig übernommen. Das heißt, ich führe von Vorlesungen über Praktika bis hin zur Prüfung das gesamte Modul durch. Dies komplementiert meine Forschungsarbeiten mit der Lehre, weshalb auch Studenten von den Arbeiten in der Forschung profitieren können und die Relevanz des Moduls aus nächster Nähe erleben können.

# Öffentlichkeitsarbeit

Was wohl am ehesten noch als Öffentlichkeitsarbeit hier zählt, ist die Betreuung der Vorlesung rund um Kryptologie. Dort kann aktiv die Forschung und Relevanz im Bereich Kryptologie beworben werden und die Relevanz des Themas hervorgehoben werden.

Nicht nur, dass im Austausch mit den Studenten Themen der Forschung beworben werden, es werden ebenfalls Themen der Forschung unmittelbar in die Lehre eingebaut, sodass die Studenten vertraut mit der aktuellen Themen der Kryptologie gemacht werden und potenziell mit Abschluss des Studiums Potenziale in diesem Bereich heben kann. Weiterhin wird auf die interdisziplinären Anwendungen hingewiesen, sodass diese schwergewichtigen Themen (Kryptologie, Künstliche Intelligenz) unter Studenten mehr Aufmerksamkeit erfahren.

# Netzwerke

Wie bereits vorher festgehalten, sind berufliche Tätigkeiten nach der Promotion noch in weiterer Ferne. Neben den vorher genannten Perspektiven ist ebenfalls die Lehre eine Möglichkeit sich beruflich zu verwirklichen und die nächsten Generationen anständig und motiviert auszubilden.