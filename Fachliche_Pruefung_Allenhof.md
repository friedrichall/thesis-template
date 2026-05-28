# Fachliche Überprüfung der Bachelorarbeit

**Arbeit:** „KI-gestützte Transformation statischer in interaktive 3D-Objekte durch Benutzerinteraktion" (Friedrich Allenhof, TH Nürnberg, Medieninformatik)
**Prüfdatum:** 27. Mai 2026
**Fokus:** Ausschließlich fachliche Korrektheit der zitierten Aussagen, Konsistenz der Zahlen, Eignung der Quellenwahl. Stilistische, sprachliche oder strukturelle Aspekte sind nicht Gegenstand dieser Prüfung.

---

## 1. Zusammenfassende Einschätzung

Die Arbeit zitiert insgesamt sorgfältig und greift überwiegend auf Primärliteratur zurück, die fachlich tatsächlich zum jeweiligen Argument passt (LLMR, Holodeck, ArtLLM, ArtiWorld, URDFormer, 3D-LLM, PointLLM, Peng et al. zu Halluzinationen). Auch die im Implementierungsteil genannten OpenAI-Modellbezeichner inklusive Snapshot-Datums sind korrekt. Die internen Evaluationszahlen sind arithmetisch konsistent (53/60 → 88,3 %; 57/60 → 95,0 %; 4 reparierte / 3 gescheiterte Durchläufe).

Drei Fundstellen sollten vor der Abgabe inhaltlich nachjustiert werden:

1. **Fehlattribution Su et al. 2015 (MVCNN) als Beleg für MLLM-Verhalten** — sachlich falsch.
2. **Übergeneralisierung von Zhang et al. 2025 („Lost-in-the-Middle in Long-Text Generation")** — die zitierte Aussage entspricht nicht exakt dem, was die Quelle zeigt.
3. **Ungeeignete Quelle für die Grunddefinition eines LLM (Lazer et al. 2026, eine Cybersecurity-Survey)** — die Quelle stützt die Aussage zwar nicht falsch, ist aber thematisch fern.

Daneben gibt es einige kleinere, eher als Hinweise zu wertende Punkte (Baran/Popović als Mesh-Beleg, Shoham 1993 als Agentendefinition, Datenflusszahlen). Details unten.

---

## 2. Kritische Befunde (sollten korrigiert werden)

### Befund A — Su et al. 2015 belegt keinen MLLM-Befund

**Stelle:** Kapitel 5, Abschnitt „Vorverarbeitung in Unity" (Z. 125):

> „Im Anschluss daran rendert Unity für das übergeordnete GameObject verschiedene Ansichten, da die Erkennungsleistung eines MLLM steigt, wenn statt einer Einzelansicht mehrere gerenderte Ansichten eines 3D-Objekts verwendet werden~\cite{suMultiviewConvolutionalNeural2015}."

**Problem:** Su, Maji, Kalogerakis und Learned-Miller (CVPR 2015, „Multi-view Convolutional Neural Networks for 3D Shape Recognition") zeigen den Effekt für **CNN-basierte 3D-Klassifikation**, nicht für **Multimodal Large Language Models**. MLLMs gibt es zum Erscheinungszeitpunkt der Arbeit (2015) nicht. Die Übertragung „CNN → MLLM" ist eine Hypothese, kein Befund der Quelle. Wörtlich heißt es im Abstract: *„we present a standard CNN architecture trained to recognize the shapes' rendered views… Recognition rates further increase when multiple views of the shapes are provided."*

**Empfehlung:** Entweder die Aussage umformulieren auf „Die Erkennungsleistung von Bildklassifikatoren auf 3D-Formen steigt mit der Anzahl gerenderter Ansichten" und mit Su et al. belegen, **oder** zusätzlich eine MLLM-spezifische Quelle ergänzen, die multi-view Inputs für MLLMs untersucht (z. B. neuere Arbeiten zu Multi-View Prompting bei VLMs). So wie es jetzt formuliert ist, ist es eine sachliche Fehlattribution.

---

### Befund B — Zhang et al. 2025 belegt nicht ganz, was die Arbeit behauptet

**Stelle:** Kapitel 4, Abschnitt 4.2.2 (Begründung des modularen Workflow-Ansatzes), Z. 114:

> „Bei einfachen LLM-Aufrufen sinkt empirisch die Regelbefolgung bei wachsender Länge und Abhängigkeit strukturierter Ausgaben, sodass halluzinierte Referenzen und unzulässige Elementtypen kaum vermeidbar wären~\cite{zhangLostintheMiddleLongTextGeneration2025}."

**Problem:** Zhang et al. 2025 („Lost-in-the-Middle in Long-Text Generation") zeigt das *Lost-in-the-Middle*-Phänomen für **lange Eingaben**, deren mittlerer Teil von LLMs übersehen wird, und schlägt mit RAL-Writer eine Mitigation vor. Die Aussage „Regelbefolgung sinkt bei wachsender Länge und Abhängigkeit strukturierter Ausgaben" generalisiert auf Schema-/Constraint-Treue strukturierter Ausgaben — das ist nicht der Untersuchungsgegenstand der Quelle. Was die Quelle korrekt belegt, ist eher: *„Lange Inputs führen dazu, dass mittig platzierte Informationen vergessen/übersehen werden."*

**Empfehlung:** Entweder die Aussage präzisieren auf „mittig platzierte Constraints werden in langen Inputs leichter übersehen" (dann passt Zhang et al.), oder zusätzlich eine Quelle ergänzen, die explizit Constraint-/Schema-Treue strukturierter LLM-Ausgaben empirisch untersucht (z. B. Arbeiten zu „structured output reliability" oder „instruction following with constraints"). Wie sie jetzt steht, ist die Aussage nicht durch die zitierte Quelle gedeckt.

---

### Befund C — Lazer et al. 2026 ist eine fachlich entfernte Quelle für die LLM-Definition

**Stelle:** Kapitel 2.4, Abschnitt „Definition" (Z. 67):

> „Large Language Models (LLMs) sind tiefe neuronale Netzwerke, welche die Verarbeitung von natürlicher Sprache ermöglichen~\cite{lazerSurveyAgenticAI2026}."

**Problem:** Lazer et al. 2026 ist eine *„Survey of Agentic AI and Cybersecurity"* — Schwerpunkt: Cybersecurity-Use-Cases agentischer Systeme. Die Arbeit nimmt LLMs als bekannt an und ist keine LLM-Grundlagenquelle. Die Aussage selbst ist korrekt, aber für eine fachliche Grundlagenstelle ungeeignet zitiert.

**Empfehlung:** Hier kanonischere Belege verwenden — z. B. Vaswani et al. 2017 („Attention is All you Need", liegt im Zotero-Ordner unter `EV4F25UH` bzw. `ZUDWY3DY` ohnehin bereit), Bommasani et al. 2022 (`QDDI29WS`) oder Zhao et al. 2026 („A Survey of Large Language Models", `ITUWDZQ3`/`J2BNV6QZ`). Diese sind im Zotero-Bestand bereits vorhanden, aber an dieser Stelle nicht verwendet. Lazer et al. passt eher zum Agenten-Teil (was die Arbeit auch tut) und kann dort bleiben.

---

## 3. Hinweise (eher Feinschliff)

### Hinweis 1 — Baran & Popović 2007 als Beleg für Mesh-Grundlagen

**Stelle:** Kapitel 2.1, Z. 12:
> „Die Mesh-Geometrie besteht aus Dreiecksnetzen oder Polyeder-Darstellungen, welche die Oberfläche durch Eckpunkte (Vertices) und deren Verbindungen definieren~\cite{baranAutomaticRiggingAnimation2007a}."

Baran & Popović „Automatic Rigging and Animation of 3D Characters" (SIGGRAPH 2007) verwendet zwar Dreiecksnetze, ist aber kein Grundlagentext zu Mesh-Geometrie. Die Aussage stimmt sachlich, die Quellenwahl wäre an einem klassischen Lehrbuch (z. B. Foley/van Dam, Akenine-Möller „Real-Time Rendering" oder Botsch et al. „Polygon Mesh Processing") besser aufgehoben. Kein sachlicher Fehler, nur ein Hinweis.

### Hinweis 2 — Shoham 1993 als Agentendefinition

**Stelle:** Kapitel 2.4, Z. 72:
> „Ein Agent ist eine autonome Einheit, welche in einer Umgebung agiert, Entscheidungen trifft und auch mit anderen Agenten interagieren kann~\cite{shohamAgentorientedProgramming1993}."

Shoham 1993 definiert Agenten primär über einen *mentalen Zustand* (beliefs, decisions, capabilities, obligations) — also stärker durch Wissensrepräsentation und Sprechakttheorie, nicht so generisch wie zitiert. Die Aussage selbst ist nicht falsch, aber die kanonische, breiter formulierte Agentendefinition stammt eher von Wooldridge & Jennings 1995 („Intelligent Agents: Theory and Practice", *Knowledge Engineering Review*) oder Russell & Norvig. Wenn die Arbeit die Definition so generisch halten will, wäre diese Quelle der bessere Beleg. Kein Fehler, aber die zitierte Quelle ist enger als die Aussage suggeriert.

### Hinweis 3 — Steuer 1992 (Definition von Interaktivität)

**Stelle:** Kapitel 2.1, Z. 18: Beleg für „Auf diese 3D-Objekte kann durch Eingaben (Input) eingewirkt werden und das Objekt reagiert zustands- oder verhaltensbezogen".

Steuer 1992 definiert Interaktivität als „the extent to which users can participate in modifying the form and content of a mediated environment in real time" — also benutzer-bezogen, nicht objekt-zustandsbezogen. Der Bezug passt grob, ist aber semantisch leicht verschoben. Wenn das beibehalten wird, würde eine ergänzende Quelle aus dem HCI-/3D-Interaktion-Bereich (Hand 1997 „A Survey of 3D Interaction Techniques" — im Zotero-Bestand als `FE2UTVMI` ohnehin vorhanden, aber an dieser Stelle nicht zitiert) das Argument tragfähiger machen.

### Hinweis 4 — Toaster-Mittelwert vs. Beschreibung

**Stelle:** Kapitel 6.3.3 (Testasset Toaster) und 6.4 (Korrekturmechanismen).

In 6.3.3 steht: *„Zwei Durchläufe lösten mehrere Wiederholungszyklen aus, einer davon erreichte schließlich die maximale Versuchsanzahl von fünf."* Daraus müsste sich für die durchschnittliche Versuchsanzahl ein höherer Wert ergeben als 1,25. Rechnerisch passt 1,25 (= 25 Versuche / 20 Durchläufe) nur, wenn 18 Durchläufe je 1 Versuch hatten + 1 Durchlauf 5 Versuche + 1 Durchlauf 2 Versuche. Damit hatte der erfolgreich reparierte Durchlauf **eine** Korrekturschleife, nicht „mehrere". Das ist keine fachliche Fehlbehauptung — die Zahlen selbst stimmen —, aber die Formulierung „mehrere Wiederholungszyklen" für **zwei** Durchläufe ist mit dem Mittelwert 1,25 inkonsistent. Entweder die Formulierung („eine Korrekturschleife" statt „mehrere Wiederholungszyklen") oder die Aufschlüsselung anpassen.

### Hinweis 5 — Lampe: konsistente Aufschlüsselung

In Kapitel 6.3.1 steht *„Fünf Durchläufe benötigten mindestens eine Korrekturschleife. Davon konnten drei Durchläufe nach zwei bzw. drei Versuchen erfolgreich abgeschlossen werden. Zwei Durchläufe erreichten die maximale Versuchsanzahl von fünf."* In Tabelle 6.6 (Wirkung der Korrekturmechanismen) sind diese Zahlen (15/20 Erstversuch, 18/20 Final, 3 repariert, 2 gescheitert) konsistent. **Hier alles in Ordnung — nur zur Bestätigung.**

### Hinweis 6 — Caffagni/Yin 2024 als Beleg für MLLM-Architektur

**Stelle:** Kapitel 2.4, Z. 85: drei Hauptmodule eines MLLM (Modality-Encoder, LLM, Connector).

Beide Quellen (Yin et al. 2024 und Caffagni et al. 2024) belegen diese Dreigliederung tatsächlich — Yin et al. spricht von „modality encoder", „LLM" und „connector/projector". **Korrekt zitiert.**

### Hinweis 7 — „aktuell leistungsstärkstes Modell von OpenAI: GPT-5.5"

**Stelle:** Kapitel 5.6 (Interaction Planner), Z. 202.

Faktencheck: GPT-5.5 wurde von OpenAI am 23. April 2026 veröffentlicht, der Snapshot `gpt-5.5-2026-04-23` (Tab. 5.1 im Spec Generator) ist real, und auch `gpt-5.1-2025-11-13` sowie GPT-5.2 (Dezember 2025) sind korrekt. Die Aussage ist zum Stand 27. Mai 2026 **sachlich richtig**, sollte aber bei Abgabe ggf. nochmals geprüft werden, da OpenAI in dieser Zeit häufig Modelle nachschiebt. *(Quellen-Hinweis: OpenAI Model Release Notes, Wikipedia GPT-5.5 / GPT-5.1.)*

---

## 4. Was inhaltlich gut belegt ist (Spot-Checks)

Zur Transparenz hier die Punkte, die ich konkret an den PDFs im Zotero-Ordner überprüft habe und die fachlich korrekt zitiert sind:

- **Kallmann & Thalmann 2002 (Smart Objects):** Die Aussage, dass Logik direkt im Objekt gespeichert wird und das Dezentralisierung/Wiederverwendung ermöglicht, ist durch das Paper gedeckt (vgl. „each object encapsulates data and provides methods for data access").
- **Peng et al. 2025 (3D-LLM-Halluzinationen):** Die Aussage, dass 3D-LLMs Objekte halluzinieren bzw. falsche Beziehungen zwischen Objekten produzieren können, steht so im Abstract des Papers.
- **De La Torre et al. 2024 (LLMR):** Modul-Aufzählung (Planner, Scene Analyzer, Skill Library, Builder, Inspector) — alle fünf Module sind im LLMR-Paper namentlich vorhanden, inklusive der iterativen Code-Inspektion. Vergleich mit eigenem modularem Workflow ist sachlich korrekt.
- **Yang et al. 2024 (Holodeck):** Die Beschreibung „Grundrisse, Materialien, Fenster und Türen, Objektauswahl sowie räumliche Anordnung" mit Constraint-basierter Platzierung deckt sich mit dem Paper.
- **Wang et al. 2026 (ArtLLM):** Punktwolke → Token-Folge mit diskreten Bins (128 pro Achse), Bild/Text-Inputs über externe Generatoren in Mesh→Pointcloud konvertiert, URDF-Export — alles im Paper bestätigt.
- **Yang et al. 2025 (ArtiWorld):** Szenenbeschreibung → Identifikation artikulierbarer Objekte → URDF, an Originalkoordinaten ausgerichtet, Geometrie wird erhalten — durch Paper gedeckt.
- **Chen et al. 2024 (URDFormer):** Bildbasierte URDF-Pipeline — korrekt.
- **Hong et al. 2023 (3D-LLM):** Aufgaben „captioning, dense captioning, 3D question answering, task decomposition, 3D grounding, 3D-assisted dialog, navigation" — exakt so im Abstract.
- **Xu et al. 2025 (PointLLM) als „objektzentriert":** Trifft zu (verarbeitet *object* point clouds).
- **Bommasani et al. 2022:** Aussagen zu emergenten Fähigkeiten und Milliarden Parametern sind durch das Paper gedeckt.

---

## 5. Was ich nicht extern verifizieren konnte

- **Vivian Framework selbst** (`VivianFrameworkGitLab2021`): Quelle ist ein GitLab-Repo; die Beschreibung der Spezifikationsstruktur (InteractionElements, VisualizationElements, States, Transitions) wird durch das Repo dokumentiert, eine vollständige Schema-Prüfung war im Rahmen dieser fachlichen Prüfung nicht leistbar.
- **Eigene Evaluationsergebnisse** (60 Durchläufe, Erfolgsquoten) — rechnerisch konsistent (siehe oben), die experimentelle Reproduzierbarkeit konnte ich nicht prüfen.

---

## 6. Konkrete Korrekturvorschläge in Stichworten

| # | Ort | Aktion |
|---|---|---|
| A | Kap. 5, Vorverarbeitung Unity (Z. 125) | „MLLM" → „CNN-basierte Bilderkennung" oder zusätzliche MLLM-Quelle ergänzen |
| B | Kap. 4.2.2, Z. 114 | Aussage zu „Regelbefolgung bei strukturierten Ausgaben" entweder enger an Lost-in-the-Middle formulieren oder zusätzliche Quelle zu Schema-Treue ergänzen |
| C | Kap. 2.4, Z. 67 | Statt Lazer et al. 2026: Vaswani et al. 2017, Bommasani et al. 2022 oder Zhao et al. 2026 (alle im Zotero-Bestand vorhanden) |
| H1 | Kap. 2.1, Z. 12 | Optional: Baran/Popović durch klassischen Mesh-Lehrbuchverweis ersetzen |
| H2 | Kap. 2.4, Z. 72 | Optional: Wooldridge & Jennings 1995 als alternative/zusätzliche Agentendefinition |
| H4 | Kap. 6.3.3 | „Mehrere Wiederholungszyklen" → „eine Korrekturschleife" für den erfolgreich reparierten Toaster-Durchlauf (oder umgekehrt: Mittelwert prüfen) |

---

## 7. Gesamtbewertung der fachlichen Korrektheit

Die fachliche Substanz der Arbeit ist solide. Die zentralen Quellen (LLMR, Holodeck, ArtLLM, ArtiWorld, URDFormer, 3D-LLM, PointLLM, Peng et al., Kallmann/Thalmann, Caffagni et al., Yin et al.) sind sachlich passend zitiert. Die drei oben genannten Befunde (A, B, C) sind keine inhaltlichen Großschäden, aber bei einer Arbeit mit gutachterlichem Anspruch lohnt sich die Korrektur, weil sie an Stellen sitzen, die bei strenger Prüfung auffallen könnten — insbesondere Befund A (Su et al. als MLLM-Beleg), der bei Fachprüfern mit Computer-Vision-Hintergrund sofort einen Pin setzt.

Die Hinweise H1–H6 sind Komfortempfehlungen und müssen nicht zwingend bearbeitet werden.
