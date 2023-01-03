Exercice 2 : Heritage 


#include iostream <br>
using namespace std;<br>
class personne<br>
{<br>
    protected :<br>
        string nom;<br><br>
        string prenom;<br>
        int age;<br>
    public:<br>
        void saisie() ;<br>
        void affichage();<br>
};<br>
class etudiant:personne<br>
{<br>
    string Tmatiere[5];<br>
    float Tnotes[5];<br>
    public:<br>
        void saisie();<br>
        float moyenne();<br>
        void affichage();<br>
};<br>
class enseignant:personne<br>
{<br>
    string Tmatiere[5];<br>
    int *Tnbh;<br>
    int tarif;<br>
    public:<br>
        void saisie();<br>
        float salaire();<br>
        void affichage();<br>
};<br>
void personne::saisie()<br>
{<br>
   <br> cout <<"Nom :";
    <br> cin>>nom;
  <br>  cout <<"Prénom :";
  <br>  cin>>prenom;
   <br> cout <<"Age :";
   <br> cin>>age;
}<br>
void personne::affichage()<br>
{<br>
    cout<<"Nom : "<<nom<<endl;<br>
    cout<<"Prenom : "<<prenom<<endl;<br>
    cout<<"age : "<<age<<endl;<br>
}<br>
void etudiant::saisie()<br>
{<br>
    personne::saisie();<br>
    for(int i=0 ; i<5 ; i++)<br>
    {<br><br>
        cout<<"Cours["<<i<<"]:";<br>
        cin>>Tmatiere[i];<br>
        cout<<"notes["<<i<<"]:";<br>
        cin>>Tnotes[i];<br>
    }<br>
}<br><br>
float etudiant::moyenne()<br>
{<br>
    int i ;<br>
    float som=0;<br>
    for (i = 0 ; i < 5 ; i++)<br>
        som = som+Tnotes[i] ;<br>
    return ( som/5 ) ;<br>
}<br>
void etudiant::affichage()<br>
{<br>
    personne::affichage();<br>
    cout<<"Matieres\tNotes"<<endl;<br>
    for(int i=0 ; i<5 ; i++)<br>
        cout<<Tmatiere[i]<<"\t\t"<<Tnotes[i]<<endl;<br>
    cout<<"La moyenne generale = "<<moyenne()<<endl;<br>
}<br>
void enseignant::saisie()<br>
{<br>
    personne::saisie();<br>
    Tnbh=new int [5];<br>
    for(int i=0 ; i<5 ; i++)<br>
    {<br>
        cout<<"Matiere["<<i<<"]:";<br>
        cin>>Tmatiere[i];<br>
        cout<<"Tnbh["<<i<<"]:";<br>
        cin>>Tnbh[i];<br>
    }<br>
    cout<<"Tarif : ";<br>
    cin>>tarif;<br>
}<br>
float enseignant::salaire()<br>
{<br>
    int i ,nbht=0;;<br>
    for (i = 0 ; i < 5 ; i++)<br>
        nbht = nbht+Tnbh[i];<br>
    return nbht*tarif ;<br>
}<br>
void enseignant::affichage()<br>
{<br><br>
    personne::affichage();<br>
    cout<<"Matieres"<<"\t"<<"Nombres d'heures"<<endl;<br>
    for(int i=0 ; i<5 ; i++)<br>
        cout<<Tmatiere[i]<<"\t\t"<<Tnbh[i]<<endl;<br>
    
    cout<<"Le tarif d'une heure = "<<tarif<<endl;
    cout<<"Le salaire = "<<salaire()<<endl;
}<br>
int main()<br>
{<br>
    etudiant e1;<br>
    enseignant ens1;<br>
    e1.saisie();<br>
    e1.affichage();<br>
    ens1.saisie();<br>
    ens1.affichage();<br>
    return 0;<br>
}<br>

  
  
  
  
  
  
 Exercice 1  
  
  
 fILE NAME :temps.h
  
#ifndef TEMPS_H_INCLUDED<br>
#define TEMPS_H_INCLUDED<br><br>
class temps{<br>
int heure;<br>
int minute;<br>
int seconde;<br><br>
public:<br>
    temps();<br>
    temps(int,int,int);<br>
    //~temps();<br>
    void afficher();<br>
    void chercher(temps);<br>
    void addition(temps);<br>
    temps ajout2();<br>
};
<br><br>

#endif // TEMPS_H_INCLUDED<br>



#include <iostream><br>
#include "temps.h"<br>
using namespace std;<br>
/*temps::~temps(){<br>
cout<<"objet detruit \n";<br>
}*/<br>
temps::temps(){<br>
heure=0;<br>
minute=0;<br>
seconde=0;<br>
}<br>
<br>temps::temps(int h,int m,int s){
<br>heure=h;
minute=m;<br>
seconde=s;<br>
}<br>
void temps::afficher(){<br>
cout<<heure<<":"<<minute<<":"<<seconde<<endl;<br><br>
}<br>
void temps::chercher(temps T2){<br>
unsigned ok=0;<br>
if (heure>T2.heure)<br>
    ok=1;<br>
if (heure==T2.heure && minute>T2.minute)<br>
    ok=1;<br>
if (heure==T2.heure && minute==T2.minute && seconde>T2.seconde)<br>
    ok=1;<br>
if (heure==T2.heure && minute==T2.minute && seconde==T2.seconde)<br>
    ok=2;<br>
switch(ok){<br>
case 0:cout<<"La premier instant vient avant le deuxieme. \n";<br>
break;<br>
case 1: cout<<"Le deuxieme instant vient avant la premier. \n";<br>
break;<br>
case 2:cout<<"il s'agit d'un meme temp .";<br>
}<br>
<br>
}<br>


  
  
 main.cpp 
  
#include <iostream><br>
#include "temps.h"<br>
using namespace std;<br>

int main()<br>
{<br>
   temps T1;<br>
   temps T2(01,05,12);<br>
   cout<<"l'horaire T1 =";<br>
   T1.afficher();<br><br><br><br>
    cout<<"l'horaire T2 =";<br><br>
   T2.afficher();<br>
   T1.chercher(T2);<br>


}<br>
