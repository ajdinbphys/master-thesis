# master-thesis
## Dataset 
5000 radiografskih snimaka pluca. Train/Test/Val split je 60/20/20. Pokušavao sam i sa 80/10/10 ali bolji rezultati su dobiveni s 60/20/20. Mislim da ovakav split odgovara bolje manjim datasetovima. Klasna distribucija nije ravnomjerna. Više je PNEUMONIA (65%) slika ali razlika nije ekstremna. 

## Model_1 (bez augmentacije)
CNN model jednostavne arhitekture - nekoliko Conv layera (uz maxpooling) i na kraju fully-connected NN s dva layera kao klasifikator. Input slike se prije učenja smanjuju na 256x256. Pokušavao sam i s manjim dimenzijama što ubrzava učenje ali overfitting brzo postaje problem. Isto tako sam testirao različite brojeve epoha, batch veličine i različite veličine parametara (različite brojeve filtera). Trenutni model se čini optimalnim. Rezultati su iznenađujuće dobri ali ipak (što se vidi na vizualizacijama; val loss raste a val accuracy ne prati train accuracy) dolazi do overfittinga.

## Model_2 (sa augmentacijom)
Sličan prvom modelu uz sljedeće modifikacije. Model_2 je dublji što je odgovor na augmentaciju slika (proširivanje dataseta) i dodan je dropout layer kao dodatna regularizacija. Augmentacija slika ne smije biti prevelika u smislu da pojedini parametri, ako se ne odaberu pažljivo, poput rotation_range, mogu nerealno izobličiti dataset što smanjuje performans na val datasetu i uzrokuje prevelike oscilacije. Broj epoha je također veći zbog augmentacije.
Rezultati su bolji u odnosu na Model_1. Accuracy je porastao sa 95.5% na 96.5%. Val loss i accuracy bolje prate train loss i accuracy respektivno.