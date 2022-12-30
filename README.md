// projet-c
// projet demandé sur github 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct date{
    int j;
    int m;
    int an;
};
struct voy{
int id;
char dest[100] ;
struct date ddep;
struct date dar;
char hotel[100] ;
int duree;
char desc[2000];
char visa[3];
int prix;

};
int n=0;
struct voy tab[1000];
int day(struct date d){
    return d.j+d.m*30+d.an*12*30;
}
void ajouter(){
    struct voy v;
    printf("Entrer l'id du voyage : ");//zidou l unicité here
    scanf("%i",&v.id);
    printf("Entrer la destination du voyage : ");
    scanf("%s",v.dest);
    printf("Entrer la date du depart du voyage (jj/mm/aaaa): ");
    scanf("%i %i %i",&v.ddep.j,&v.ddep.m,&v.ddep.an);
    printf("Entrer la date d'arriver du voyage (jj/mm/aaaa) : ");
    scanf("%i %i %i",&v.dar.j,&v.dar.m,&v.dar.an);
    printf("Entrer l'hotel du voyage : ");
    scanf("%s",v.hotel);
    printf("Visa demandée (oui/non) : ");
    scanf("%s",v.visa);
    /*
        durée a faire
    */
    printf("Entrer la description du voyage : ");
    scanf("%s",v.desc);

    printf("Entrer le prix du voyage : ");
    scanf("%i",&v.prix);
    tab[n]=v;
    n+=1;
}
void supp(int iden){
    int test=0;
    for(int i=0;i<n;i++){
        if (tab[i].id== iden){
            for(int j=i;j<n-1;j++)
                tab[i]=tab[i+1],test=1;
            n-=1;
            break;
        }

    }
    if(!test){
        printf("pas de voyage \n");
    }

}
void recherche(struct date dd, struct date da){
    int found = 0;
    printf("Voyages disponibles entre le %d/%d/%d et le %d/%d/%d :\n", dd.j, dd.m, dd.an, da.j, da.m, da.an);
    for(int i=0; i<n; i++){
        if(day(dd)>=day(tab[i].ddep)&&day(da)<=day(tab[i].dar)){
                printf("ID : %d\n", tab[i].id);
                printf("Destination : %s\n", tab[i].dest);
                printf("Date de départ : %d/%d/%d\n", tab[i].ddep.j, tab[i].ddep.m, tab[i].ddep.an);
                printf("Date d'arrivée : %d/%d/%d\n", tab[i].dar.j, tab[i].dar.m, tab[i].dar.an);
                printf("Hôtel : %s\n", tab[i].hotel);
                printf("Durée : %d\n", tab[i].duree);
                printf("Description : %s\n", tab[i].desc);
                printf("Visa demandé : %s\n", tab[i].visa);
                printf("Prix : %d\n", tab[i].prix);
                found = 1;
        }
    }
    if(!found){
        printf("Aucun voyage disponible entre les dates données.\n");
    }
}


void afficher(int iden){
    int found = 0;
    for(int i=0; i<n; i++){
        if(tab[i].id == iden){
            found = 1;
            printf("ID : %d\n", tab[i].id);
            printf("Destination : %s\n", tab[i].dest);
            printf("Date de départ : %d/%d/%d\n", tab[i].ddep.j, tab[i].ddep.m, tab[i].ddep.an);
            printf("Date d'arrivée : %d/%d/%d\n", tab[i].dar.j, tab[i].dar.m, tab[i].dar.an);
            printf("Hôtel : %s\n", tab[i].hotel);
            printf("Durée : %d\n", tab[i].duree);
            printf("Description : %s\n", tab[i].desc);
            printf("Visa demandé : %s\n", tab[i].visa);
            printf("Prix : %d\n", tab[i].prix);
            break;
        }
    }
    if(!found){
        printf("Aucun voyage trouvé avec l'ID %d\n", iden);
    }
}


void modifier(int iden){
    int found = 0;
    for(int i=0; i<n; i++){
        if(tab[i].id == iden){
            found = 1;
            printf("Entrez la nouvelle destination du voyage : ");
            scanf("%s", tab[i].dest);
            printf("Entrez la nouvelle date de départ du voyage (jj/mm/aaaa) : ");
            scanf("%d %d %d", &tab[i].ddep.j, &tab[i].ddep.m, &tab[i].ddep.an);
            printf("Entrez la nouvelle date d'arrivée du voyage (jj/mm/aaaa) : ");
            scanf("%d %d %d", &tab[i].dar.j, &tab[i].dar.m, &tab[i].dar.an);
            printf("Entrez le nouvel hôtel du voyage : ");
            scanf("%s", tab[i].hotel);
            printf("Entrez la nouvelle durée du voyage : ");
            scanf("%d", &tab[i].duree);
            printf("Entrez la nouvelle description du voyage : ");
            scanf("%s", tab[i].desc);
            printf("Entrez si un visa est maintenant nécessaire (oui/non) : ");
            scanf("%s", tab[i].visa);
            printf("Entrez le nouveau prix du voyage : ");
            scanf("%d", &tab[i].prix);
            break;
        }
    }
    if(!found){
        printf("Aucun voyage trouvé avec l'ID %d\n", iden);
    }
}
void lkol(){
    for(int i=0; i<n; i++){
            printf("ID : %d\n", tab[i].id);
            printf("Destination : %s\n", tab[i].dest);
            printf("Date de départ : %d/%d/%d\n", tab[i].ddep.j, tab[i].ddep.m, tab[i].ddep.an);
            printf("Date d'arrivée : %d/%d/%d\n", tab[i].dar.j, tab[i].dar.m, tab[i].dar.an);
            printf("Hôtel : %s\n", tab[i].hotel);
            printf("Durée : %d\n", tab[i].duree);
            printf("Description : %s\n", tab[i].desc);
            printf("Visa demandé : %s\n", tab[i].visa);
            printf("Prix : %d\n", tab[i].prix);
        }
}

int main()
{
    int iden;
    n=0;
    int faza;
    struct date dd;
    struct date da;
    printf("donner la valeur de faza\n");
    scanf("%i",&faza);
    while(faza!=0)
    {
        if (faza==1)
        {
            //cv
            ajouter();

        }
        else if(faza==-1){
            //cv
            lkol();
        }
        else if (faza==2)
        {
         //cv
          printf("donner l'identificateur\n");
          scanf("%i",&iden);
          supp(iden);
        }
         else if (faza==3)
        {
          //cv
          printf("Entrer la date du depart  (jj/mm/aaaa): ");
          scanf("%i %i %i",&dd.j,&dd.m,&dd.an);
          printf("Entrer la date d'arriver  (jj/mm/aaaa) : ");
          scanf("%i %i %i",&da.j,&da.m,&da.an);
          recherche(dd, da);
        }
         else if (faza==4)
        {
         printf("donner l'identificateur a afficher\n");
         scanf("%i",&iden);
         //cv
         afficher(iden);
        }
         else if (faza==5)
        {
            //cv
         printf("donner l'identificateur a modifier\n");
         scanf("%i",&iden);
         modifier(iden);
        }
        else if (faza==0)
        {
            //cv
            printf("quitter le menu \n");
            break;
        }

        //cv
        printf("donner faza again \n");
        scanf("%i",&faza);
    }

    return 0;
}
