# PLC_Project

# Descrizione
Mini linea automatizzata sviluppata in TwinCAT 3 per simulare un sistema industriale.

## Architettura

Il progetto è strutturato secondo un'architettura modulare:

- MAIN: coordinamento della logica macchina
- FB: gestione attuatori (motore, valvola)
- TYPES: definizione enum e stati
- GVL: segnali globali (I/O simulati)

## Logica di funzionamento

- Il sensore rileva un pezzo sul nastro
- Dopo un ritardo viene attivata la valvola
- La valvola esegue apertura/chiusura tramite state machine
- Il motore gestisce avviamento, running e fault

## Caratteristiche
- Structured Text (TwinCAT 3)
- State machine per attuatori
- Gestione fault (timeout, interlock)
- Simulazione segnali
