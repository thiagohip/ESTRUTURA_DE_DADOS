# ESTRUTURA_DE_DADOS

ATIVIDADE 01 - JOGO DA FORCA


string wsort(int wlen, string words[]){
    int n;
    string w;
    n = rand()%wlen;
    w = words[n];
    return w;
};

string bars(string w){
    string wlock; wlock = "";
    for (int i = 0; i<w.length(); i++){
        wlock += "_"; }

    return wlock;
};

string lcheck(char l, string w, string wlock, bool *ach){
    *ach = false;
    for (int i=0; i<w.length(); i++){
        if (w[i] == l){
            wlock[i] = l;
            *ach = true; }
    } return wlock;
};

bool wincheck(string w, string wlock){
    bool acertou;
    acertou = true;
    for(int i = 0; i<w.length(); i++){
        if(wlock[i] == '_'){
            return false;
        }
    }
    return acertou;
};

void result(string wlock, bool acerto){
                cout << wlock;
                if(acerto){
                    cout << endl;
                    cout << "Parabéns, você acertou a palavra!" << endl;
                }else{
                    cout << endl;
                    cout << "Infelizmente, você não conseguiu acertar a palavra!" << endl;
                }
            }

int menu(){
        int op;
        cout << "=-==-==-==-==-==-==-==-==-==-==-==-==-==-==-=" << endl;
        cout << " Bem vindo ao jogo da forca " << endl;
        cout << "=-==-==-==-==-==-==-==-==-==-==-==-==-==-==-=" << endl;
        cout << "[1]Começar a jogar" << endl;
        cout << "[2]Sair do jogo" << endl;
        cin >> op;
        return op;
    }

void hud(string wlock, int erros){
                    cout << wlock << endl;
                    cout << "Erros: " << erros << endl;
                    cout << "Informe uma letra: ";
                }

const int WLEN = 20;

int main(){
    string words[WLEN] = {"abacateiro", "estrela", "gravata", "forca", "dromedario", "julieta", "janela", "geladeira", "hemorragia", "paralelepipedo", "corrida", "safira", "amendoa", "amarela", "abelha", "clava", "trovoada", "ondulado", "calmaria", "servente"};
    string w, wlock;
    char l, esc;
    int erros, i, n;
    bool ach, acerto;
    srand(time(NULL));
    //Menu inicial.
    int op;
    op = menu();
    //----------------------------------------//
    if(op == 1){
        do{
            //Sortear uma palavra do dicionário.
            w = wsort(WLEN, words);
            //----------------------------------------//
            //Encher a palavra escondida de barras.
            wlock = bars(w);
            //----------------------------------------//
            erros = 0;
            acerto = false;
            do{
                system("clear");
                //HUD
                hud(wlock, erros);
                //----------------------------------------//
                cin >> l;
                //Verificação de acerto da letra.
                wlock = lcheck(l, w, wlock, &ach);
                if (!ach){
                    erros++;
                }
                //----------------------------------------//
                //Verificar se a palavra ja foi encontrada
                acerto = wincheck(w, wlock) ;
                //----------------------------------------//
            }while(erros < 6 && !acerto);
            //Resultado.
            result(wlock, acerto);
            //----------------------------------------//
            cout << "Quer continuar jogando? [S/N]";
            cin >> esc;
        }
        while(esc == 's' || esc == 'S');
        cout << "Jogo finalizado!";
        }else if(op == 2){
            system("clear");
            cout << "Jogo finalizado!";
            system("exit");
        }
    return 0;
}
