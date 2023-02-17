# ESTRUTURA_DE_DADOS

ATIVIDADE 01 - JOGO DA FORCA


/******************************************************************************

                              Online C++ Compiler.
               Code, Compile, Run and Debug C++ program online.
Write your code in this editor and press "Run" button to compile and execute it.

*******************************************************************************/

#include <iostream>

using namespace std;

#include <iostream>
#include <string.h>
#include <math.h>
using namespace std;

string bars(string w){
    string wlock;
    wlock = "";
    for (int i = 0; i<w.length(); i++){
        wlock += "_";
    }
    return wlock;
}

string lcheck(char l, string w, string wlock, bool *ach){
    *ach = false;
    for (int i=0; i<w.length(); i++){
            if (w[i] == l){
                wlock[i] = l;
                *ach = true;
            }   
        }
    return wlock;
}


int main(){
string words[20] = {"abacateiro", "estrela", "gravata", "forca", "dromedario", "julieta",
"janela", "geladeira", "hemorragia", "paralelepipedo", "corrida", "safira", "amendoa",
"amarela", "abelha", "clava", "trovoada", "ondulado", "calmaria", "servente"};

string w, wlock;
char l, esc;
int erros, i, j, n;
bool acerto, ach;

srand(time(NULL));
cout << "=-==-==-==-==-==-==-==-==-==-==-==-==-==-==-=" << endl;
cout << "         Bem vindo ao jogo da forca          " << endl;
cout << "=-==-==-==-==-==-==-==-==-==-==-==-==-==-==-=" << endl;
cout << "Pressione ENTER para jogar.";
cin.ignore().get();
system("clear");
do{
    n = rand()%20;
    w = words[n];
    wlock = bars(w);
    
    erros = 0;
    acerto = false;
    do{
        system("clear");
        
        cout << wlock << endl;
        cout << "Erros: " << erros << endl;
        cout << "Informe uma letra: ";
        cin >> l;
        
        wlock = lcheck(l, w, wlock, &ach);
        
        
        if (!ach)
            erros++;
        j = 0;
        for(i = 0; i<w.length(); i++){
            if(wlock[i] == '_'){
                j++;
            }
        }
        if (j==0)
            acerto = true;
    }while(erros < 6 && !acerto);
    
    cout << wlock;
    if(acerto){
        cout << "Parabéns, você acertou a palavra!";
    }else{
        cout << "Infelizmente, você não conseguiu acertar a palavra!";
    }
    cout << "Quer continuar jogando? [S/N]";
    cin >> esc;
}while(esc == 's' || esc == 'S');
cout << "Jogo finalizado!";
return 0;
}
