# Rapport d'audit — à compléter

Auteur :Anais
Date :09/11/26
Référence de départ (commit) :commit documentaire

| ID constat | Règle CT | Fichier et fonction | Reproduction / observation | Impact | Priorité P0/P1/P2 | Action (corriger / surveiller / différer) |
|---|---|---|---|---|---|---|
| A-01 |CT-06 | src/feess.js: calculateShippingFee | (0, 'FR') -> reçu 4, attendu RangeError/ (1,'XX') -> NaN alors que attendu RangeError| Facturation sur entrée interdite, sortie non numerique| P1 | Corriger avec 3 tests initialement: weight: 0, infinity et Zone: 'XX'|
| A-02 |CT-02 | src/shipment.js: advanceShipment | created -> 'delivered' -> accepté, attendu Error / prepared -> 'prepared' -> accepté, attendu Error| Parcours sauté ou répété, historique incohérent| P1 | Corriger avec 3 tests initialement: sautée, répétée et arrière|
| A-03 |CT-03 | src/shipment.js: advanceShipment, cancelShipment | canceled -> 'prepared' -> accepté, attendu Error / cancel(canceled) -> accepté, attendu Error| Colis annulé réactivable, état terminal non protégé| P1 | Corriger avec 2 tests initialement: canceled -> prepared et canceled -> cancel|
| A-04 |CT-07 | src/tracking.js: getPublicTracking | vue publique -> contient recipientEmail, attendu reference/status/history| Fuite du courriel| P0 | Corriger avec 2 tests: clés exactes et historique copié|
| A-05 |CT-08 | src/php/TrackingPresenter.php: publicCard | carte publique -> contient recipientEmail, attendu reference/statusLabel| Fuite du courriel| P0 | Corriger avec 2 tests: clés exactes et libellés conservés|
| A-06 |CT-04 | src/shipment.js: cancelShipment | in_transit -> cancel -> accepté, attendu Error| Colis en transit annulable| P1 | Corriger avec 3 tests: in_transit refusé, created et prepared acceptés|

## Dette différée et justification

## Contrôles avant modification

## Contrôles après modification

## Limites et risques résiduels
