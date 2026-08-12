\# Trading Report Tool



Strumenti in Python per generare report fiscali chiari e ordinati a partire

dai dati di trading su piattaforme MetaTrader, pensati come ausilio alla

dichiarazione dei redditi e concepiti per essere comprensibili anche da chi non

opera nel settore (commercialista, CAF, uffici competenti).



\*\*Software proprietario - tutti i diritti riservati. Vedi \[LICENSE](LICENSE).\*\*



\---



\## A cosa serve



Chi opera in trading su forex e CFD si trova spesso con estratti conto tecnici,

in valuta estera e di difficile lettura per chi deve gestirne gli aspetti fiscali.

Questo progetto trasforma quei dati grezzi in un report Excel strutturato,

con operazioni, totali calcolati e un glossario esplicativo integrato.



Il report chiarisce fin da subito i punti che generano più fraintendimenti - ad

esempio che le operazioni "BUY" e "SELL" su strumenti come oro o coppie di valute

NON corrispondono ad acquisti o vendite fisiche di beni, ma a contratti

finanziari (CFD) il cui unico esito è un profitto o una perdita in denaro.



\---



\## Struttura del progetto



trading-report-tools/

|-- README.md

|-- LICENSE

|-- .gitignore

|-- MetaTrader5/ strumenti per MetaTrader 5

|-- MetaTrader4/ strumenti per MetaTrader 4





Tutti i moduli condividono lo stesso motore di analisi e producono lo stesso

formato di report Excel a quattro fogli. Cambia solo la sorgente dei dati.



\---



\## MetaTrader5/



\### report-tool-mt5-open-app



Nota: questo è il primo approccio del progetto, mantenuto come prototipo

funzionante della connessione live via API. Per l'uso corrente si utilizza il

modulo "da file" descritto sotto.



Versione live: si collega al terminale MT5 aperto e loggato sul PC, scarica

lo storico delle operazioni per un periodo scelto, ricostruisce i trade completi

e produce il report Excel. Legge però lo storico solo dalla cache locale del

terminale e non può forzarne il caricamento dal server: l'intervallo va quindi

impostato prima nella Cronistoria del terminale e poi, una seconda volta, nel

notebook. Questa doppia impostazione è tra le ragioni che hanno portato a

preferire il modulo "da file".

Adatta a chi ha il terminale MT5 disponibile e può tenerlo aperto durante

l'esecuzione.



\### report-tool-mt5-from-file



Modulo definitivo per l'uso corrente. Analizza un report di cronistoria MT5

esportato in formato .xlsx, senza bisogno di tenere il terminale aperto. Stesso

motore e stesso report della versione live, ma con l'intervallo di date già

contenuto nell'estratto: si imposta una sola volta, nel terminale, al momento

dell'esportazione.

Adatta a chi non può o non vuole tenere l'applicazione aperta, o deve elaborare

estratti forniti da terzi.



Funzionalità principali:

\- Individuazione automatica del file esportato da MT5 nella cartella

\- Estrazione delle operazioni già abbinate da MT5 (apertura + chiusura)

\- Separazione tra operazioni di trading e movimenti di cassa (depositi/prelievi)

\- Lettura automatica dei dati del conto dall'intestazione del file

\- Calcolo del profitto netto dei costi del broker (commissioni + swap)



\---



\## MetaTrader4/



\### report-tool-mt4-from-file



Analisi dell'estratto conto MT4 esportato in formato .htm, con lo stesso motore

di analisi e lo stesso formato di report degli altri moduli. MetaTrader 4 non

dispone della connessione diretta via Python, quindi il flusso è sempre da file.



\---



\## Report Excel prodotto



Ogni modulo genera un file .xlsx con quattro fogli:



\- Operazioni - dettaglio di ogni trade (strumento, volume, date, profitto)

\- Riepilogo - dati del conto e totali fiscali, calcolati con formule

\- Movimenti di cassa - depositi e prelievi, tenuti separati dai trade

\- Guida e glossario - spiegazioni a corredo per il lettore del report



\---



\## Requisiti



\- Windows con terminale MetaTrader installato (per il modulo MT5 live)

\- Python 3.12 (ambiente Miniconda consigliato)

\- Pacchetto ufficiale MetaTrader5 (solo per il modulo MT5 live)

\- pandas, openpyxl



\---



\## Note



\- Tutti gli importi sono espressi nella valuta del conto (tipicamente USD).

L'eventuale conversione in euro e gli adempimenti fiscali (quadro RW, imposta

di bollo, ecc.) sono di competenza dello studio commercialistico.

\- Questi strumenti organizzano ed espongono i dati; NON costituiscono

consulenza fiscale.



\---



Copyright 2026 Nicola Vessio - Tutti i diritti riservati.

