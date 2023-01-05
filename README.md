# Kelas-Struktur-data
#fligth

#ifndef FLIGHT_H_INCLUDED
#define FLIGHT_H_INCLUDED
#include <iostream>
#define info(P) P->info
#define next(P) P->next
#define first(L) (L).first
#define nil NULL

using namespace std;

struct jadwalPenerbangan{
    string kode;
    string jenis;
    string tanggal;
    string waktu;
    string asal;
    string tujuan;
    int kapasitas;

};

typedef struct element *adr;
typedef jadwalPenerbangan infotype;

struct element{
    infotype info;
    adr next;
};

struct List{
    adr first;
};

void createList_1301210260(List &L);
adr createElemen_1301210260(infotype x);
void insertLast_1301210260(List &L,adr P);
void showJadwal_1301210260(List L);
void deleteFirst_1301210260(List L,adr &P);
adr searchJadwal_1301210260(List L,string dari,string kemana,string tanggal);


#endif // FLIGHT_H_INCLUDED


#include "flight.h"

void createList_1301210260(List &L){
    first(L) = nil;
}

adr createElemen_1301210260(infotype x){
    adr P = new element;
    info(P) = x;
    next(P) = nil;
    return P;
}

void insertLast_1301210260(List &L,adr P){
    if(first(L) == nil){
        first(L) = P;
    }else{
        adr Q = first(L);
        while(next(Q) != nil){
            Q = next(Q);
        }
        next(Q) = P;
    }
}

void showJadwal_1301210260(List L){
    adr P;
    P = first(L);
    int i = 1;
    while(P != nil){
        cout<<i<<"." <<"Kode : " <<info(P).kode <<endl;
        cout<<" " << "Jenis : " << info(P).jenis << endl;
        cout<<" " << "Tanggal : " << info(P).tanggal << endl;
        cout<<" " << "Waktu: " << info(P).waktu << endl;
        cout<<" " << "Asal : " << info(P).asal << endl;
        cout<<" " << "Tujuan : " << info(P).tujuan << endl;
        cout<<" " << "Kapasitas : " << info(P).kapasitas << endl;
        cout<< "===================" << endl;
        P = next(P);
        i++;
    }
}

void deleteFirst_1301210260(List L,adr &P){
    P = first(L);
    first(L) = next(P);
    next(P) = nil;
}

adr searchJadwal_1301210260(List L,string dari,string kemana,string tanggal){
    adr P = first(L);
    while(P != nil && info(P).asal != dari && info(P).tujuan != kemana && info(P).tanggal != tanggal){
        P = next(P);
    }
    return P;
}






#include "flight.h"



int main()
{
    List L;
    createList_1301210260(L);
    infotype X;
    adr P;
    X.kode = "QG680";
    X.jenis = "Airbus A320";
    X.tanggal = "8 Desember 2022";
    X.waktu = "04.55";
    X.asal = "Jakarta (CGK)";
    X.tujuan = "Denpasar (DPS)";
    X.kapasitas = 180;
    P = createElemen_1301210260(X);
    insertLast_1301210260(L,P);
    X.kode = "QG250";
    X.jenis = "ATR 72600";
    X.tanggal = "9 Desember 2022";
    X.waktu = "12.55";
    X.asal = "Surabaya (SUB)";
    X.tujuan = "Malang (MLG)";
    X.kapasitas = 25;
    P = createElemen_1301210260(X);
    insertLast_1301210260(L,P);
    //adr prec = searchJadwal_1301210260(L,"Surabaya","Malang","9 Desember 2022");
    //insertLast_1301210260(L.prec);
    showJadwal_1301210260(L);
    return 0;
}

