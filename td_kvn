/*Objectif :
Créer un programme où l'utilisateur doit deviner un nombre aléatoire généré par l'ordinateur. Le programme doit inclure un menu interactif avec des choix et des structures switch, if, et else if.

Instructions :

Le programme commence par afficher un menu avec trois options :

1 : Jouer au jeu
2 : Règles du jeu
3 : Quitter
Si l'utilisateur choisit "1 : Jouer au jeu" :

Le programme génère un nombre aléatoire entre 1 et 100.
L'utilisateur doit deviner ce nombre.
Après chaque tentative, le programme indique si le nombre saisi est "trop grand", "trop petit" ou "correct".
Le programme continue jusqu'à ce que l'utilisateur trouve le bon nombre.
Si l'utilisateur choisit "2 : Règles du jeu" :

Le programme affiche une description des règles du jeu :
"Un nombre aléatoire est généré entre 1 et 100. Votre objectif est de le deviner en recevant des indices après chaque tentative. Bonne chance !"

Si l'utilisateur choisit "3 : Quitter" :

Le programme affiche un message de fin et s'arrête.
Si l'utilisateur entre un choix invalide, le programme doit afficher un message d'erreur et réafficher le menu.

Bonus :

Sauvegarder le nombre de fois que l'utilisateur a réussi a trouver le nombre, 
si le nombre est inférieur a celui sauvegarder on demande son nom et on sauvegarde les deux informations.

dans chaque debut de partie on affiche le nom et le nombre de fois que l'utilisateur a réussi a trouver le numéro

Sauvegarder les deux informations dans un fichier pour lors de la prochaine partie cela réaffiche le score et le nom de l'utilisateur*/




/*Bonus 2 :
- Optimiser le code
- Ajouter des commentaires
- gestion des erreurs
- gestion users
- easter egg*/


// Inclusion des bibliothèques
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>
#include <locale.h>


// Fonction pour afficher le message secret
void secretMessage() {
    printf("\n Félicitations, vous avez trouvé l'easter egg !\n");
}


// Fonction principale
int main(){
    // Variables
    int choix, choixE;
    int fautes, Streaks, nbu, count;
    int ascii_values[] = {101, 97, 115, 116, 101, 114}; // Correspond à 'e', 'a', 's', 't', 'e', 'r'
    int repI1, repI2;
    int repIV1, repIV2, repIV3;
    int rate, rate2;
    int indice1, indice2, indice3;
    char NomMVP[50], NomA[50];

    // Varwhile
    int RepJeu1, RepJeu2, RepJeu3;
    int tempC, tempo;
    int RepUtilisateur;
    int infini = 1;


    // Code caché pour l'easter egg (mot spécifique via manipulation ASCII)
    char input[100];
    int code = 0xabcdef; // code mystérieux

    
    setlocale(LC_ALL, "fr_FR.UTF-8"); //Def UTF-8
    

    printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
    printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
    printf("////////////////////////////////////// Bienvenus sur le jeu de devinette ! /////////////////////////////////////////////////////////////\n");
    printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
    printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
    
    printf("\n Entrez votre nom : \n"); // l'utilisateur rentre son nom
    scanf(" %s", NomA);
    FILE *fichier;

    //verifier le fichier s'il existe
    fichier = fopen("score.txt", "r");
    if (fichier != NULL){
        fscanf(fichier," %s %d", NomMVP, &Streaks);
        fclose(fichier);
        printf("\n Le meilleur score est détenu par %s avec %d essais.\n", NomMVP, Streaks);
    }
    else if (fichier == NULL){
        printf("Erreur lors de l'ouverture du fichier.\n"); // Si le fichier n'existe pas, aucun meilleur score n'a été enregistré
    }
    else {
        printf("Pas de meilleur score enregistré.\n"); // Si le fichier n'existe pas, aucun meilleur score n'a été enregistré
    }

    //initialisation du programme
    while (tempo != 1){
        printf("/////////////////////////////////////////////////////\n");
        printf("/////////////////////////////////////////////////////\n");
        printf("///////////// Voici le Menu du Jeu : ////////////////\n");
        printf("/////////////////////////////////////////////////////\n");
        printf("/////////////////////////////////////////////////////\n");

        printf("1. Jouer au Jeu\n 2. Regles du Jeu \n 3. Quitter\n");

        if (scanf(" %d", &choix) != 1){
            printf("\n Erreur de saisie.\n");
            while(getchar() != '\n');
            continue;
        }

        srand(time(NULL));
        int nba = rand() % 100; // récuperer un nb aléatoire entre 1 et 100

        switch(choix){
            case 1 :     
                while (RepUtilisateur != 1){
                    printf("Entrez un nombre entre 1 et 100 : \n");
                    if (scanf("%d", &nbu) != 1) { //si le nombre n'est pas un nombre correct
                        printf("Entree invalide ! Veuillez entrer un nombre entier.\n");
                        while (getchar() != '\n');  // vider le buffer
                        continue;  //pour recommencer la boucle -> optimisation du code
                    }

                    if (nbu < 1 || nbu > 100){ //si le nombre n'est pas compris dans la plage donnée
                        printf("Le nombre n'est pas compris dans la plage donnee.\n");
                    }
                    else if (nbu < nba){ //si le nombre est trop petit
                        printf("\n Le nombre est trop petit.\n");
                        fautes++;
                    } 
                    else if (nbu > nba){ //si le nombre est trop grand
                        printf("\n Le nombre est trop grand.\n");
                        fautes++;
                    } 
                    else { //si le nombre est correct
                        printf("\n Vous avez trouvez le nombre.\n");
                        RepUtilisateur = 1;
                    }
                }
                if (fautes < Streaks){ //si le nombre de fautes est inférieur au nombre de fautes de la partie precedente
                    printf("\n Bravo vous avez fait mieux que le meilleur score !\n");
                    printf("\n Entrez votre nom : \n");
                    scanf(" %s", NomA);

                    fichier = fopen("score.txt", "w");
                    if (fichier != NULL){
                        fseek(fichier, 0, SEEK_SET);  // Aller au début du fichier
                        fprintf(fichier, "%s %d", NomA, fautes);
                        fclose(fichier);
                    }
                    else {
                        printf("Erreur lors de l'ouverture du fichier.\n");
                    }
                }          
            break;
            case 2 : //Règles du jeu
                printf("\n Un nombre aleatoire est genere entre 1 et 100. \n Votre objectif est de le deviner en recevant des indices apres chaque tentative. \n Bonne chance ! \n");
            break;
            case 3 : //Quitter
                printf("///////////////////////////////////////////////////////////////////\n");
                printf("///////////////////////////////////////////////////////////////////\n");
                printf("//////////////////// Votre partie à été enregistree ///////////////\n");
                printf("///////////////////////////////////////////////////////////////////\n");                            
                printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");              
                printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");  
                printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
                printf("///////////////////////////       ///   ////   ///         /////       ///   ////   ///         ////////////////////////////////////////\n");
                printf("//////////////////////////  ////  ///  ///  /////  ////////////  ////  ///  ///  /////  ////////////////////////////////////////////////\n");
                printf("/////////////////////////  ////  ///  ///  ////  /////////////  ////  ///  ///  ////  //////////////////////////////////////////////////\n");
                printf("////////////////////////         ///  /  ////       /////////         ///  /  ////       ///////////////////////////////////////////////\n");
                printf("///////////////////////  ////  /////   /////  //////////////  ////  /////   /////  /////////////////////////////////////////////////////\n");
                printf("//////////////////////  ////  /////   ////  ///////////////  ////  /////   ////  ///////////////////////////////////////////////////////\n");
                printf("/////////////////////       //////   ///         /////////       //////   ///         //////////////////////////////////////////////////\n");
                printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
                printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");
                printf("////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////\n");

                tempC = 1;
                tempo = 1;
                return 0;
            break;
            case 4 :
                printf("\n Veuillez choisir la difficulté de l'easter egg (niveau 1 = '1' ; niveau 2 = '2') \n");
                scanf(" %d", choixE);
                if (choixE == 1){
                    // Affiche chaque caractère en utilisant son code ASCII
                    for (int i = 0; i < 6; i++) {
                        printf(" %c", ascii_values[i]);

                        rate++;
                        if (rate % 3 == 0) {
                            printf("\nVoulez-vous un indice ? '1' Oui '2' Non \n");
                            scanf(" %d", &repI1);
                        
                            if(repI1 == 1){
                                printf("\n Pour trouver cet 'easter egg' il faut connaître le tableau ASCII. \n Bonne chance XD \n");
                            }
                            else {
                                printf("\n Bonne Chance \n");
                            }
                        }   
                    }
                    printf("\n");
                }
                else if (choixE == 2){
                    printf("\n Entrez un mot : \n");
                    fgets(input, sizeof(input), stdin);

                    // Nettoyer l'entrée pour éviter les sauts de ligne à la fin de l'entrée
                    input[strcspn(input, "\n")] = '\0';

                    // Condition cachée: vérifier si l'entrée correspond à un mot spécifique
                    // mais en combinant un hash et une manipulation sur les valeurs ASCII des caractères
                    for (int i = 0; input[i] != '\0'; i++) {
                        code ^= input[i] << (i % 8);
                        rate++;

                        if (rate % 3 == 0) {
                            // Demander l'indice 1
                            printf("\n Voulez-vous un indice ? '1' Oui '2' Non \n");
                            scanf(" %d", &repIV1);

                            if (repIV1 == 1 && !indice1) {
                                printf("\n Indice 1 : La clé pour découvrir le secret réside dans les caractères que tu choisis et leur position. \n Chaque caractère a son propre poids, et l'alignement parfait des bits est nécessaire si tu veuX dévoiler le message caché. \n");
                                indice1 = 1;
                            } 
                            else if (repIV1 == 2) {
                                printf("\n Bonne chance ! \n");
                            }
                            if (indice1) {
                                // Demander l'indice 2
                                printf("\n Voulez-vous un autre indice ? '1' Oui '2' Non \n");
                                scanf(" %d", &repIV2);

                                if (repIV2 == 1 && !indice2) {
                                    printf("\n Indice 2 : Le mot que tu cherches a 6 lettres. \n Pour le trouver, pense à des mots courants et teste-les. \n L'Ordre des lettres est crucial, et chaque caractère doit être 'juste'. \n Essaie des mots qui sont un peu spéciaux pour toi. \n");
                                    indice2 = 1;
                                } 
                                else if (repIV2 == 2) {
                                    printf("\n Bonne chance ! \n");
                                }
                                if (indice2) {
                                    // Demander l'indice 3
                                    printf("\n Voulez-vous un autre indice ? '1' Oui '2' Non \n");
                                    scanf(" %d", &repIV3);
                                    if (repIV3 == 1 && !indice3) {
                                        printf("\n Indice 3 : Le mot est créé de manière aléatoire, mais chaque lettre a sa propre valeur. \n La position de chaque lettre modifie le résultat. \n Essaie des mots simples, mais attention à chaque caractère et à son rôle. \n","\n"," \n Parfois «il faut savoir líre entre les lïgnes afin de trouver d’autres indices. \n Per aspera ad astra. \n");
                                        indice3 = 1;
                                    } 
                                    else if (repIV3 == 2) {
                                        printf("\n Bonne chance ! \n");
                                    }
                                }
                            }
                        }
                    }
                    printf("\n");
                }

                // Si la condition cachée est remplie, afficher le message secret
                if (code == 0x123456) {
                    secretMessage();
                }
                else {
                    printf("\n Faux ! \n");
                }  
            break;
            default : //Choix Invalide
                printf("\n Choix Invalide.\n");
            break;
        }     
    }
}