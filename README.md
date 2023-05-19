**Data**

**CTG-classification**

Cardiotocography Data Set from the UCI Machine Learning repository, reperibile alla URL seguente: https://archive.ics.uci.edu/ml/datasets/Cardiotocography#

Trattasi di un problema di classificazione *multiclass*, il cui fine è quello di predire lo stato di salute del feto rappresentata dalla variabile “NSP”.  

Le classi sono distribuite nel modo seguente: 
  - Normale
  - Sospetto
  - Patologico
  - Goals

Le seguenti domande hanno guidato la nostra analisi:
Quale modello di Machine Learning risulta più efficace per questo dataset?
Quali sono i parametri che abbiamo utilizzato nella valutazione della performance dei modelli discussi?
Quali conclusioni possiamo trarre dall’adozione di uno dei modelli testati rispetto alla natura del problema? 

**Analisi esplorativa**

Al fine di poter applicare i nostri modelli di Machine Learning al dataset, abbiamo effettuato le seguenti operazioni sul dataframe:
  - Eliminazione di righe contenenti solo valori NaN e di colonne irrilevanti.
  - Trasformazione del tipo dei dati (data type) da object a float.

La prima considerazione è quella che il dataset risulta essere non bilanciato (*imbalanced*). Questo aspetto ci ha portato a considerare con attenzione differenti metriche per la valutazione degli algoritmi testati e non soltanto l’accuratezza. 

Dopo un esame dei diagrammi a scatola e baffi, abbiamo con cautela eliminato alcune osservazioni contenenti outliers per la feature “AC”.  

Il risultato è stato poi un generale miglioramento della performance dei vari modelli, in particolare della recall e precision.
Inoltre, un’analisi delle correlazioni ha evidenziato come alcune features (per esempio, “ASTV” e “ALTV”) abbiano una correlazione moderata con la variabile dipendente “NSP”.

**Modelli**

Abbiamo testato i seguenti modelli di Machine Learning che sono classicamente utilizzati in problemi di natura classificatoria:
  
  - KNN
  - Logistic Regression
  - Random Forest
  - Gradient Boosting Classifier

Per ognuno di questi algoritmi è stata implementata una convalida incrociata utilizzando la tecnica di *Grid Search* al fine di individuare gli iperparametri ottimali.

**Performance**

Una volta selezionati i parametri migliori per ciascuno di questi algoritmi, abbiamo istanziato modelli basati su di essi e giudicato la loro performance utilizzando metriche standard quali accuratezza, precisione, richiamo e f1. Come già anticipato, poiché il dataset non è bilanciato abbiamo valutato attentamente non semplicemente l’accuratezza del modello, ma anche, per esempio, la sua capacità di richiamo.
I risultati migliori sono stati ottenuti in ordine decrescente:

 - Gradient Boosting Classifier 
 - Random Forest
 - KNN
 - Logistic Regression

Questo ordine non ci sorprende, vista la generale migliore capacità di algoritmi basati sull’apprendimento d’insieme (*ensemble learning*) di catturare relazioni non lineari e ignorare casi estremi.

Un aspetto da tenere in considerazione è anche i tempi di allenamento e predizione di un modello. Data la maggiore complessità computazionale dei modelli di apprendimento d'insieme, i migliori modelli nella nostra lista sono anche quelli che richiedono più tempo nella fase di allenamento. In particolare, il *Gradient Boosting Classifier* che abbiamo considerato ha richiesto un tempo di allenamento molto più grande di quello del *Random Forest*, per cui i suoi ottimi risultati andrebbero commisurati al tipo di applicazione che si intende implementare.

**Conclusioni finali**

Alcune considerazioni finali. Innanzitutto, il fatto che il dataset non sia bilanciato richiederebbe uno studio più approfondito dei casi estremi e del loro trattamento di quanto sia stato possibile fare in questo esercizio. Alternativamente, si potrebbero provare tecniche di *over-sampling*, al fine di ottenere una distribuzione più bilanciata. 

Vi sono vari possibili utilizzi del nostro migliore algoritmo che abbiamo testato (il *Gradient Boosting* ma vale anche per *il Random Forest*) . Quelli più ovvi sono la possibilità di aiutare il personale medico nel fornire diagnosi e interventi precoci più efficaci. Inoltre, questo tipo di modello permette di identificare le features più importanti e ciò potrebbe contribuire alla creazione di dataset meno sensibili a rumore statistico.






