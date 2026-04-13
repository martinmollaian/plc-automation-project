# PLC Automation Project – Conveyor & Ejection System

## Descrizione
Progetto PLC sviluppato in TwinCAT 3 (Structured Text) che simula una mini linea automatizzata composta da un nastro trasportatore e una stazione di espulsione.

L’obiettivo è riprodurre logiche tipiche industriali: gestione attuatori, coordinamento macchina, fault handling e simulazione segnali.

---

## Architettura

Il progetto è strutturato secondo un’architettura modulare:

- **MAIN**
  - Coordinamento della logica macchina tramite state machine
  - Gestione sequenze operative ed eventi

- **FB_Motor**
  - Controllo motore con stati: IDLE, STARTING, RUNNING, STOPPING, FAULT
  - Gestione timeout di avviamento e perdita feedback
  - Gestione warning

- **FB_Valve**
  - Controllo valvola con stati: IDLE, OPENING, OPENED, CLOSING, CLOSED, FAULT
  - Gestione timeout apertura/chiusura
  - Controllo coerenza feedback (diagnostica errore)

- **TYPES**
  - Definizione ENUM per stati e codici errore

- **GVL**
  - Gestione segnali globali (I/O simulati)

---

## Logica di funzionamento

1. Il sistema entra in stato RUN tramite comando Start
2. Il motore avvia il nastro trasportatore
3. Un sensore rileva il pezzo in arrivo
4. Dopo un ritardo temporizzato, viene attivata la valvola
5. La valvola esegue una sequenza di apertura e chiusura per espulsione
6. Il sistema monitora eventuali fault e passa in stato di errore se necessario

---

## Caratteristiche tecniche

- Linguaggio: Structured Text (IEC 61131-3)
- Architettura modulare basata su Function Block
- Implementazione di state machine per attuatori e macchina
- Gestione eventi tramite edge detection (`R_TRIG`)
- Utilizzo di timer IEC (`TON`) per sequenze temporizzate
- Simulazione dei segnali per test senza hardware

