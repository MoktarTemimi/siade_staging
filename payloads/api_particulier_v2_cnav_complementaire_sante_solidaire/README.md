# Statut complémentaire santé solidaire (C2S)
* [200-beneficiaire_avec_participation-feminin.yaml](200-beneficiaire_avec_participation-feminin.yaml)

  Status `200`

  ## Bénéficiaire AVEC participation financière - féminin

Ce cas permet de tester :
- [Param. appel] lieu de naissance en France
- [Param. appel] sexe féminin
- [Param. appel] Deux prénoms
- [Réponse] statut bénéficiaire de la complémentaire santé solidaire AVEC participation financière

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "codeInseeLieuDeNaissance": "08480",
    "codePaysLieuDeNaissance": "99100",
    "sexe": "F",
    "nomNaissance": "DUPONT",
    "prenoms": [
      "JEANNE",
      "LAURE"
    ],
    "anneeDateDeNaissance": 1993,
    "moisDateDeNaissance": 8
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "beneficiaire_avec_participation_financiere",
    "dateDebut": "2023-06-01",
    "dateFin": "2024-06-01"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'codeInseeLieuDeNaissance=08480' -d 'codePaysLieuDeNaissance=99100' -d 'sexe=F' -d 'nomNaissance=DUPONT' -d 'prenoms[]=JEANNE' -d 'prenoms[]=LAURE' -d 'anneeDateDeNaissance=1993' -d 'moisDateDeNaissance=8' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [200-beneficiaire_sans_participation-masculin-pays_etranger.yaml](200-beneficiaire_sans_participation-masculin-pays_etranger.yaml)

  Status `200`

  ## Bénéficiaire SANS participation financière - masculin - né dans un pays étranger

Ce cas permet de tester :
- [Param. appel] Pays de naissance autre que la France
- [Param. appel] sexe masculin
- [Param. appel] Deux prénoms
- [Réponse] statut bénéficiaire de la complémentaire santé solidaire SANS participation financière

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "codeInseeLieuDeNaissance": "08481",
    "codePaysLieuDeNaissance": "99127",
    "sexe": "M",
    "nomNaissance": "DUPONT",
    "prenoms": [
      "PIERRE",
      "PAUL"
    ],
    "anneeDateDeNaissance": 1984,
    "moisDateDeNaissance": 12
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "beneficiaire_sans_participation_financiere",
    "dateDebut": "2023-02-01",
    "dateFin": "2024-02-01"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'codeInseeLieuDeNaissance=08481' -d 'codePaysLieuDeNaissance=99127' -d 'sexe=M' -d 'nomNaissance=DUPONT' -d 'prenoms[]=PIERRE' -d 'prenoms[]=PAUL' -d 'anneeDateDeNaissance=1984' -d 'moisDateDeNaissance=12' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [200-non-beneficiaire_masculin.yaml](200-non-beneficiaire_masculin.yaml)

  Status `200`

  ## Non bénéficiaire - masculin

Ce cas permet de tester :
- [Param. appel] lieu de naissance en France
- [Param. appel] sexe masculin
- [Réponse] statut non-bénéficiaire de la complémentaire santé solidaire

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "codeInseeLieuDeNaissance": "08480",
    "codePaysLieuDeNaissance": "99100",
    "sexe": "M",
    "nomNaissance": "DUPONT",
    "prenoms": [
      "PIERRE"
    ],
    "anneeDateDeNaissance": 1966,
    "moisDateDeNaissance": 6
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "non_beneficiaire_css",
    "dateDebut": "null",
    "dateFin": "null"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'codeInseeLieuDeNaissance=08480' -d 'codePaysLieuDeNaissance=99100' -d 'sexe=M' -d 'nomNaissance=DUPONT' -d 'prenoms[]=PIERRE' -d 'anneeDateDeNaissance=1966' -d 'moisDateDeNaissance=6' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [404.yaml](404.yaml)

  Status `404`

  Dossier non trouvé

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "nomNaissance": "DUBOCHE",
    "codeInseeLieuDeNaissance": "00404",
    "codePaysLieuDeNaissance": "99100",
    "sexe": "F"
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "error": "not_found",
    "reason": "Dossier allocataire inexistant. Le document ne peut être édité.",
    "message": "Dossier allocataire inexistant. Le document ne peut être édité."
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'nomNaissance=DUBOCHE' -d 'codeInseeLieuDeNaissance=00404' -d 'codePaysLieuDeNaissance=99100' -d 'sexe=F' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [503.yaml](503.yaml)

  Status `503`

  Timeout - délai d'attente dépassé

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "nomNaissance": "DUBOCHE",
    "prenoms": [
      "JEROME"
    ],
    "codeInseeLieuDeNaissance": "00503",
    "codePaysLieuDeNaissance": "99100",
    "sexe": "F"
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "error": "network_error",
    "reason": "timeout of 10000 ms exceeded",
    "message": "Une erreur est survenue lors de l'appel au fournisseur de donnée"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'nomNaissance=DUBOCHE' -d 'prenoms[]=JEROME' -d 'codeInseeLieuDeNaissance=00503' -d 'codePaysLieuDeNaissance=99100' -d 'sexe=F' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [beneficiaire_avec_participation_financiere_etranger_femme_200.yml](beneficiaire_avec_participation_financiere_etranger_femme_200.yml)

  Status `200`

  ## Bénéficiaire né à l'étranger sans participation financière femme - 200

Ce cas permet de tester :
- [Param. appel] Nom d'usage
- [Param. appel] Nom de naissance
- [Param. appel] Deux prénoms
- [Param. appel] Date de naissance (jour,mois,année)
- [Param. appel] sexe féminin
- [Réponse] statut bénéficiaire de la complémentaire santé solidaire SANS participation financière

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "nomUsage": "PLUSSE",
    "nomNaissance": "GERVINAT",
    "prenoms": [
      "MADELEINE",
      "LEA"
    ],
    "anneeDateDeNaissance": 1976,
    "moisDateDeNaissance": 8,
    "jourDateDeNaissance": 24,
    "codeInseeLieuDeNaissance": null,
    "codePaysLieuDeNaissance": "99131",
    "sexe": "F"
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "beneficiaire_sans_participation_financiere",
    "dateDebut": "2024-10-01",
    "dateFin": "2025-10-01"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'nomUsage=PLUSSE' -d 'nomNaissance=GERVINAT' -d 'prenoms[]=MADELEINE' -d 'prenoms[]=LEA' -d 'anneeDateDeNaissance=1976' -d 'moisDateDeNaissance=8' -d 'jourDateDeNaissance=24' -d 'codeInseeLieuDeNaissance=' -d 'codePaysLieuDeNaissance=99131' -d 'sexe=F' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [beneficiaire_avec_participation_financiere_femme_200.yml](beneficiaire_avec_participation_financiere_femme_200.yml)

  Status `200`

  ## Bénéficiaire avec participation financière femme - 200

Ce cas permet de tester :
- [Param. appel] Nom d'usage
- [Param. appel] Nom de naissance
- [Param. appel] Deux prénoms
- [Param. appel] Date de naissance (jour,mois,année)
- [Param. appel] sexe féminin
- [Réponse] statut bénéficiaire de la complémentaire santé solidaire AVEC participation financière

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "nomUsage": "DUPUIS",
    "nomNaissance": "CARTIER",
    "prenoms": [
      "CELINE",
      "MARIE"
    ],
    "anneeDateDeNaissance": 1980,
    "moisDateDeNaissance": 10,
    "jourDateDeNaissance": 10,
    "codeInseeLieuDeNaissance": "75056",
    "codePaysLieuDeNaissance": "99100",
    "sexe": "F"
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "beneficiaire_avec_participation_financiere",
    "dateDebut": "2024-06-01",
    "dateFin": "2025-06-01"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "X-Api-Key: $token" \
    -G -d 'nomUsage=DUPUIS' -d 'nomNaissance=CARTIER' -d 'prenoms[]=CELINE' -d 'prenoms[]=MARIE' -d 'anneeDateDeNaissance=1980' -d 'moisDateDeNaissance=10' -d 'jourDateDeNaissance=10' -d 'codeInseeLieuDeNaissance=75056' -d 'codePaysLieuDeNaissance=99100' -d 'sexe=F' \
    --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire"
  ```

  </p>
  </details>
* [fake_france_connect_cnaf.yml](fake_france_connect_cnaf.yml)

  Status `200`

  Cas de test pour CSS avec jeton FranceConnect.
Les données proviennent de [nos propres jetons FranceConnect de test](../france_connect/cnaf_css.yml).
L'endpoint est appellé avec le jeton FranceConnect + le recipient.

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "prenoms": [
      "Georges"
    ],
    "nomNaissance": "CNAF",
    "anneeDateDeNaissance": 2002,
    "moisDateDeNaissance": 1,
    "jourDateDeNaissance": 1,
    "sexe": "M",
    "codeInseeLieuDeNaissance": "75002",
    "codePaysLieuDeNaissance": "99100"
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "beneficiaire_sans_participation_financiere",
    "dateDebut": "2021-05-05",
    "dateFin": "2023-03-03"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "Authorization: Bearer $token_france_connect" --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire?recipient=13002526500013"
  ```

  </p>
  </details>
* [france_connect_cnaf.yml](france_connect_cnaf.yml)

  Status `200`

  Cas de test pour CSS avec jeton FranceConnect.
Les données proviennent des jetons de l'environnement de test FranceConnect.
L'endpoint est appellé avec le jeton FranceConnect + le recipient.

  <details><summary>Paramètres</summary>
  <p>

  ```json
  {
    "prenoms": [
      "Angela",
      "Claire",
      "Louise"
    ],
    "nomNaissance": "DUBOIS",
    "anneeDateDeNaissance": 1962,
    "moisDateDeNaissance": 8,
    "jourDateDeNaissance": 24,
    "sexe": "F",
    "codeInseeLieuDeNaissance": "75107",
    "codePaysLieuDeNaissance": "99100"
  }
  ```

  </p>
  </details>

  <details><summary>Réponse API</summary>
  <p>

  ```json
  {
    "status": "beneficiaire_sans_participation_financiere",
    "dateDebut": "2023-02-01",
    "dateFin": "2024-02-01"
  }
  ```

  </p>
  </details>

  <details><summary>Commande cURL</summary>
  <p>

  ```bash
  curl -H "Authorization: Bearer $token_france_connect" --url "https://staging.particulier.api.gouv.fr/api/v2/complementaire-sante-solidaire?recipient=13002526500013"
  ```

  </p>
  </details>
