# Documentation d'utilisation pour l'application BlocParser

#### Description générale :
Ces quatre scripts Rust fonctionnent ensemble pour interagir avec un nœud Bitcoin à l'aide de commandes RPC via `bitcoin-cli`. L'utilisateur peut choisir d'exécuter différents modules pour récupérer des informations sur les transactions Bitcoin ou les blocs. Le script principal (`main.rs`) sert de point d'entrée et permet de sélectionner et d'exécuter l'un des trois autres scripts : `parser1.rs`, `parser2.rs`, et `txparser.rs`.

#### Structure des scripts :

1. **main.rs** : Point d'entrée principal qui propose à l'utilisateur de choisir le script à exécuter. Les options incluent `parser1`, `parser2`, et `txparser`. Si des arguments sont fournis à l'exécution, ils déterminent directement quel script doit être exécuté.

2. **parser1.rs** :
   - Ce script récupère un bloc Bitcoin spécifique à partir de son hash en interrogeant le nœud via RPC.
   - Il extrait et affiche des informations comme la version du bloc, le hash du bloc précédent, le Merkle root, l'horodatage (converti en format lisible), le nombre de transactions, et des détails sur le nonce et les bits.

3. **parser2.rs** :
   - Ce script interroge un nœud Bitcoin pour récupérer l'en-tête d'un bloc à partir d'un hash de bloc.
   - Les informations récupérées sont affichées en format JSON, directement issues du nœud.

4. **txparser.rs** :
   - Ce script permet de récupérer les détails d'une transaction Bitcoin spécifique en fournissant l'ID de la transaction (TXID) et le hash du bloc contenant cette transaction.
   - Il extrait et affiche les informations détaillées de la transaction, comme le nombre d'entrées/sorties, la version de la transaction, le lock time, et le montant total des sorties.

#### Pré-requis :
- Un nœud Bitcoin fonctionnel avec `bitcoin-cli` installé.
- Un fichier `.env` contenant les variables d'environnement `RPC_USER` et `RPC_PASSWORD` pour l'authentification RPC avec le nœud Bitcoin.

#### Utilisation :

1. **Exécution sans arguments :**
   - Si vous exécutez le programme sans fournir d'arguments, il vous proposera un menu interactif pour choisir le script à exécuter :
     ```bash
     cargo run
     ```
   - Le programme affichera les options suivantes :
     ```
     Quel script voulez-vous exécuter ?
     1. Parser1
     2. Parser2
     3. Txparser
     4. Quitter
     ```
   - Entrez le numéro correspondant à l'option souhaitée et suivez les instructions.

2. **Exécution avec arguments :**
   - Vous pouvez directement indiquer le script à exécuter via des arguments en ligne de commande :
     ```bash
     cargo run parser1
     ```
   - Ce mode d'exécution rapide permet de lancer un script sans passer par le menu interactif.

#### Détails supplémentaires :
- **Hash de bloc et ID de transaction valides pour les tests :**
   - Bloc : `00000000000000000003208c8ad11e9507848536b7b2c68e34a679ac138920fa`
   - Transaction : `72f062588496755ce8f1ed4e6b12eca0ad9ea5118d5fa75698692bd101748cf0`

