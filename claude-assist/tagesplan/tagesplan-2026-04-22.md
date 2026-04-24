# Tagesplan — 22. April 2026

**Phase:** Konzeption (16.04.–25.04.) — noch **3 Tage** in der Phase · **23 Tage** bis zum internen Termin (15.05.)
**Nächste Phase:** Implementierung startet morgen (23.04.) — Überlappung beginnt jetzt.

---

## Seit gestern geändert

Keine Dateiänderungen seit Montag (20.04.).
Zuletzt bearbeitet wurden `2_grundlagen.tex` (Mo 13:28) und `3_stand_der_forschung.tex` (Mo 17:37) — offenbar ein produktiver Montag, danach Pause.

---

## ⚠️ Drift-Warnung

`4_methodik.tex` hat aktuell 53 Wörter — im Wesentlichen eine Einleitungszeile und drei leere Abschnittsköpfe.
Die Konzeptionsphase endet in drei Tagen, die Implementierungsphase startet morgen.
Ohne einen ausformulierten Methodik-Abschnitt fehlt morgen die konzeptionelle Grundlage, auf der die Implementierung aufbauen kann.
Das ist der kritische Engpass des Tages.

---

## Tagesportionen

**1 · `4_methodik.tex` — Anforderungsanalyse & Zielsetzung ausformulieren**

Füll die leeren Abschnitte `\section{Anforderungsanalyse}` und `\subsection{Zielsetzung}` mit konkretem Inhalt.
Was sind die funktionalen Anforderungen an die Pipeline (strukturell korrekte Spezifikationen, multimodale Eingabe, iterative Fehlerkorrektur, Nutzer\*innen-Feedback)?
Ziel: 2–3 Absätze, die klar machen, _was_ das System leisten muss — nicht wie, das kommt im nächsten Abschnitt.
Deliverable: `\subsection{Zielsetzung}` hat Text, der auch als Grundlage für die Einleitung taugt.

**2 · `4_methodik.tex` — Ideenentwicklung: Pipeline-Architektur als Prosa skizzieren**

`\section{Ideenentwicklung}` ist komplett leer.
Schreib hier den groben Ablauf der Pipeline auf: Wie kommt das 3D-Bild/die Szene als Input rein?
Welche LLM-Schritte durchläuft es?
Wo greift der Feedback-Loop?
Das muss keine finale Architektur sein — eine strukturierte Prosa-Skizze reicht, damit du morgen beim Implementierungsstart weißt, was du bauen willst.
Deliverable: 1–2 Absätze, die den Kern-Ansatz festhalten.

**3 · `1_einleitung.tex` — Problemstellung (erste Fassung)**

Der Abschnitt `\section{Problemstellung}` ist leer.
Jetzt, wo Grundlagen und Stand der Forschung stehen, ist der richtige Moment für eine erste grobe Fassung: Welches Problem löst die Arbeit?
(Statische 3D-Objekte ohne Verhaltensbeschreibung; manuelle Spezifikationserstellung für Vivian ist aufwendig und fehleranfällig; fehlende Automatisierung.)
Deliverable: 3–5 Sätze — kein Perfektionismus, einfach das Problem klar benennen.

---

## Beobachtung

`3_stand_der_forschung.tex` — Abschnitt „Einordnung der vorliegenden Arbeit" — hat nur zwei Sätze.
Das reicht als Platzhalter, aber der Abschnitt trägt noch nicht die argumentative Last, die er später haben sollte (Abgrenzung zum Stand der Forschung, Legitimation des eigenen Ansatzes).
Kein Handlungsbedarf heute, aber im Hinterkopf behalten.
