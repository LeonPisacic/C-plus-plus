#include <iostream>
#include <string>
#include <vector>
#include <fstream>
#include <sstream>
using namespace std;

/*Napisite funkciju PONAVLJANJE koja u zadanoj rijeci tipa string odredi koja slova su zapisana vise puta
u zadanoj rijeci. Funkcija kao rezultat vraca vektor s popisom tih slova
Prototip funkcije: vector<char>PONAVLJANJE(string rijec);
primjer: ako je rijec: abcdaxcw
rezultat funkcije->vektor:a,c

vector<char>PONAVLJANJE(string rijec) {

	vector<char>a;
	int brojac = 0;
	char TrazenoPonavljajuceSlovo;
	

	int v = 1;
	for (int i = 0; i < rijec.length(); i++) {
		for (int j = i + 1; j < rijec.length(); j++) {
			if (rijec[i] == rijec[j]) {
				TrazenoPonavljajuceSlovo = rijec[i];
				cout << TrazenoPonavljajuceSlovo << " , ";
				brojac++;
				a.push_back(TrazenoPonavljajuceSlovo);
			}
		}
		v = 1;
	}
	
	if (brojac == 0) {
		cout << "Nema ponavljajucih slova! " << endl;
	}
	if (brojac != 0) {
		cout << endl;
		cout << "---------------------------------------------------------" << endl;
		cout << "Broj brojeva koji se ponavljanju vise puta je :" << brojac << endl;
		return a;
	}

	//ovo je ukoliko zelim da mi program ispise svako ponavljanje odredenog slova, u tom slucaju makivamo 26 liniju koda

	/*	for (int k = 0; k < a.size(); k++) //prolazim kroz vektor
	{
		cout << a.at(k) << endl; //ispisujem elemente vektora na poziciji k
	}
	return a; //vracam vektor
}

int main() {

	string rijec;


	cout << "Unesi rijec u program :";
	getline(cin, rijec);

	PONAVLJANJE(rijec); //pozivanje funckije
}
*/

/*Napisi funkciju UPIS koja upise preko tipkovnice u vektor imena osoba.
Upisivanje zavrsava kada korisnik posalje prazan string u vektor.
Na kraju funkcija ispise poruku koliko imena je upisano u vektoru
void UPIS(vector<string>imena);

void UPIS(vector<string>imena) {

	int brojac = 0;
	int pokusaj = 0;
	
	if (imena.size()-1 == 0) {
		cout << "Vektor je prazan! " << endl;
	}
	else {
		cout << "Broj imena zapisanih u vektoru je :" << imena.size() - 1 << endl; //moramo -1 jer program broji i prazan string
		cout << "Broj imena zapisanih u vektoru (sa praznim stringom) :" << imena.size() << endl; //ako zelimo ispis sa praznim stringom
	}
}

int main() {

	vector<string>imena;
	string ime;


	cout << "Upisi ime (unos se zavrsava kad se unesene prazan string) :" << endl;

	do {
		getline(cin, ime);
		imena.push_back(ime);

	} while (ime != "");

	UPIS(imena); //pozivanje funckije

	
}*/

/*U datoteci imena.txt zapisana su imena osoba. Napisite funckiju TRAZI_IME koja ce provjeriti da li se u datotoeci nalazi trazeno ime
Kao rezultat funckija vraca boolean vrijednost. Ulazni argument funkcije je ime tipa string
prototip funkcije: bool TRAZI_IME(string ime)

bool TRAZI_IME(string TrazenoIme) {

	ifstream datoteka;
	bool NalaziSe=true;
	string ime;
	int brojac = 0;

	datoteka.open("imena.txt");

	if (datoteka.is_open()) {

		while (getline(datoteka, ime)) {
			
			if (ime == TrazenoIme) {
				NalaziSe = true;
				brojac++;
			}
			else {
				NalaziSe = false;
			}
		}	
		cout << brojac << endl;
		datoteka.close();
	}
	return NalaziSe;
}

int main() {

	ofstream datoteka;
	string imena;
	string TrazenoIme;

	datoteka.open("imena.txt");

	if (datoteka.is_open()) {

		cout << "Unesi imena u datoteku :" << endl;
		for (int i = 0; i < 3; i++) {
			getline(cin, imena);
			datoteka << imena<<endl;
		}

		cout << "Unesite ime koje zelite pretraziti :";
		getline(cin, TrazenoIme);
	}
	else {
		cout << "Error" << endl;
	}
	TRAZI_IME(TrazenoIme); //pozivanje funckije
}
*/

/*Napisite funkciju zanmenke koja odredi koliko znamenaka u zadanom broju su visekratnici zadanog broja
funkcija kao rezultat vraca broj takvih zznamenaka. Funkcija ima dva argumenta, broj
koji se unosi te vrijednost visekratnika
Prototip funkcije: int ZNAMENKE(int broj,int visekratnik);


int ZNAMENKE(int broj, int visekratnik) {

	int novaVarijabla;
	int brojac = 0;

	do {
		novaVarijabla = broj % 10;  // npr 424 modulo od 10 je 4
		broj = broj / 10;    // ova varijabla nam samo služi da npr broj 424 pretvorimo u drugom krugu u 42, a u trecem u 4, 
		                     // u cetvrtom je kraj i izlazi se iz do while-a 

		if (novaVarijabla % visekratnik == 0) {  //4 % 2 (npr) ==0 , brojac se podigne na 1
			brojac++;
		}

	} while (broj != 0);

	cout << "U ovom broju postoje " << brojac << " visekratnika!" << endl;

	return brojac;
}

int main() {

	int broj, visekratnik;

	cout << "Unesi broj koji zelis pregledati :";
	cin >> broj;

	cout << "Unesi visekratnik koji ce pregledati prethodno izabrani broj :";
	cin >> visekratnik;

	ZNAMENKE(broj, visekratnik); //pozivanje funckije
} */


/*u datoteci gradovi.txt zapisana su imena gradova,
napisite funkciju GRAD_NA_SLOVO koja ce provjeriti koliko imena zapisanih gradova pocinju zadanim slovom.
Kao rezultat funkcija vraca cijeli broj. Ulazni argument funckije je zadano slovo.
Prototip funkcije: int GRAD_NA_SLOVO(char slovo);
primjer: Datoteka(Karlovac,Cakovec,Kranj,Zagreb)
zadano slovo je k, rezultat funkcije 2

int GRAD_NA_SLOVO(char slovo) {

	ifstream datoteka;
	datoteka.open("gradovi.txt");

	string gradovi;
	int brojac = 0;


	if (datoteka.is_open()) {
		while (!datoteka.eof()) {
			datoteka >> gradovi;
			
				if (gradovi[0] == slovo) {
					cout << gradovi << endl;
					brojac++;
				}
		}
	}
	else {
		cerr << "Error 2" << endl;
		exit(1);
	}
	cout << "Broj gradova na to početno slovo je :" << brojac << endl;
}

int main() {
	ifstream datoteka;
	datoteka.open("gradovi.txt");

	char slovo;

	if (datoteka.is_open()) {

		cout << "Upisi slovo za grad :";
		cin >> slovo;
	}
	else {
		cerr << "Error!" << endl;
		exit(1);
	}
	GRAD_NA_SLOVO(slovo); //pozivanje funckije
}*/


/*Napisite funkciju koja racuna sumu svih cijelih brojeva vecih od 100 i manjih od 300,
čiji je zbroj znamenki jednak zadanom.Funkcija ima jedan argument, zadani zbroj zanmenaka, 
Prototip funkcije: int SUMA(int zadani_zbroj);

int SUMA(int zadaniBroj) {

	int unos1,unos2, unos3;
	int Ukupno;
	int brojac = 0;

	for (int i = 100; i < 300; i++) {
		
		unos1 = i / 100;
		unos2 = (i / 10) % 10;
		unos3 = i % 10;

		Ukupno = unos1 + unos2 + unos3;
		
		if (zadaniBroj == Ukupno) {
			brojac++;
			cout << i << " , ";
		}
	}
	cout << endl;
	cout << "Broj takvih brojeva je :" << brojac << endl;
	return brojac;
}

int main() {

	int zadaniBroj;

	cout << "Upisi zadani broj :";
	cin >> zadaniBroj;

	SUMA(zadaniBroj); //pozivanje funckije
}*/

/*U dva vektora zapisani su brojevi. Napišite funkciju FORMIRAJ koja će formirati novu datoteku "brojevi.txt".
Funkcija uspoređuje međusobno brojeve koji se nalaze u vektorima te u datoteku zapiše uvijek onaj broj elementa vektora koji je veći.
Protorip funkcije:
void FORMIRAJ(vector<int>vec1,vector<int>vec2);
PR:
vektor1: 2, 4, 20, 8
vektor2: 8, 12, 4, 3
Datoteka "brojevi.txt" : 8, 12, 20, 8


void FORMIRAJ(vector<int>a, vector<int>b){
	
	ofstream datoteka;
	datoteka.open("brojevi.txt");
	int brojacA = 0;
	int brojacB = 0;


	if (datoteka.is_open()) {
		for (int i = 0; i < a.size() && i < b.size(); i++) {

			if (a[i] > b[i]) {
				cout << a[i] << " , ";
				datoteka << a[i] << " , "; //zapisivanje brojeva u datoteku
			}
			else {

				cout << b[i] << " , ";
				datoteka << b[i] << " , "; //zapisivanje brojeva u datoteku
			}
		}
	}

}

int main() {

	vector<int> a, b;
	int brojeviA, brojeviB;


	a = {2,4,20,8};
	b = {8,12,4,3};

	FORMIRAJ(a, b); //pozivanje funckije
}*/


/*U vektoru su zapisani cijeli brojevi.Napišite funkciju BRISI koja će iz
vektora obrisati onaj broj iz vektora kod kojeg se najviše puta ponavlja zadana znamenka.
Funkcija briše pronađeni broj i vraća njegovu poziciju u vektoru.
Funkcija ima dva argumenta : vektor s brojevima i vrijednost i znamenke koja se provjera u brojevima.
Protip funkcije :
int BRISI(vector<int>dana, int znamenka);
Primjer:
vektor: 123->345->111->231->121->389
znamenka : 1
obrisano vektor : 123->345->231->121->389(obrisan je broj 111 jer ima najviše znamenki 1)
Rezultat 3(broj se nalazi na 3. mjestu u vektoru)


int BRISI(vector<int>dana, int znamenka) {
	
	int max = 0;
	int unos;
	int nes;

	
	for (int i =0; i < dana.size(); i++) {

		do {
			unos = i % 10;
			i = i / 10;
		} while (dana.size());
		
		if (dana[i] == znamenka) {
			max = dana[i];
		}
	}
	 cout << "Broj s najvise znamenka je :" << max << endl;
	 return 0;
}

int main() {
	
	int brojevi,znamenka;
	vector<int>dana;

	dana = {123,345,111,231,121,389};
	
	cout << "Upisi trazeni broj koji zelis pretraziti :";
	cin >> znamenka;

	BRISI(dana,znamenka); //pozivanje funckije
} NEUSPJESNO */

/*Napišite funkciju UPIS_DATOTEKA zapisuje u datoteku "recenica.txt" re?enice koje upisuje korisnik.
U datoteku se zapisuju samo re?enice koje se sastoje od to?no zadanog broja rije?i. Ukoliko se re?enica ne sastoji od 
zadanog broja rije?i, takva re?enica se ne upisuje u datoteku. Upis završava kada korisnik tri(3) puta pogrešno upiše re?enicu.
Prototip funkcije za upis: int UPIS_DATOTEKA(int brojRijeci);


int UPIS_DATOTEKA(int brojRijeci) {

	ofstream datoteka;
	datoteka.open("recenica.txt");

	
	if (datoteka.is_open()) {

		string recenica;
		int pokusaj = 0;

		while (datoteka) {
			cin.ignore();
			getline(cin, recenica);
			int brojacRijeciURecenici = 1; //ukoliko ovo deklariramo izvan  while-a ili ivan datoteka.is_open nece raditi!!!!!

			for (int i = 0; i < recenica.length(); i++) {
				if (recenica[i] == ' ') {
					brojacRijeciURecenici++;
				}
			}
			if (brojacRijeciURecenici == brojRijeci) {
				datoteka << recenica << endl; //upis recenice u datoteku
			}
			else {
				pokusaj++;
				cout << "Greska broj " << pokusaj << endl;
				if (pokusaj == 3) {
					break;
				}

			}
		}
	}
	return brojRijeci;
}

int main() {

	int brojRijeci;

	cout << "Unesi broj rijeci koji zelis limitirati recenici :";
	cin >> brojRijeci;

	UPIS_DATOTEKA(brojRijeci); //pozivanje funckije
}*/

/*U datoteci "telefon.txt" nalaze se zapisani telefonski brojevi studenata na način
da prvo piše ime i prezime studenta, a u sljedećem redu njegov telefonski broj. Napišite
funkciju STUDENT_TELEFON koja će vratiti telefonski broj za traženo ime i prezime studenata.
Funkcija ima jedan parametar, ime i prezime studenta. Prototip funkcije:
string STUDENT_TELEFON(string student)


string STUDENT_TELEFON(string student) {


	ifstream datoteka;
	datoteka.open("Telefon.txt");
	


	if (datoteka.is_open()) {

		string pretragaStudenta;
		int brojac = 0;
		int telefonskiBroj;
	

		while (getline(datoteka, pretragaStudenta)) {
			
				cout << "Telefonski broj od osobe koji trazis :";
				while(!datoteka.eof()){
					datoteka >> telefonskiBroj;

					if (pretragaStudenta == student) {
						cout << telefonskiBroj << endl;
						break;
					}
				}
		}
		datoteka.close();
	}
	return student;
}
	

int main() {
	string student;


	cout << "Upisi nekog za pretragu njegovog telefonskog broja :";
	getline(cin, student);

	STUDENT_TELEFON(student); //pozivanje funckije
}
*/

/*Korisnik upiše riječ koja se sastoji od različitih slova bez ponavljanja.
Slova u riječi nisu poredan po abecedi. Napišite funkciju SORT koja će transformirati
upisanu riječ na način da slova budu poredane po abecedi A-Z. Funkcija vraća novu
riječ sortiranih slova. Prototip funkcije:
string SORT(string rijec);

string SORT(string rijec) {

	int n = rijec.length();
	char Preokret; //uzimamo char zato sto se radi o sortiranju slovo po slovo, a jedno slovo se iskazuje char-om

	cout << n;
	for (int i = 0; i < n; i++) {  

		for (int j = i + 1; j < n; j++) {

			if (rijec[i] > rijec[j]) {

				Preokret = rijec[i];
				rijec[i] = rijec[j];
				rijec[j] = Preokret;
            }
		}
	}
	cout << "---------------" << endl;
	cout << "Rijesenje :" << rijec << endl;
	return rijec;
}

int main() {

	string rijec;

	cout << "Upisi rijec koju zelis abacedeno okrenuti :";
	getline(cin, rijec);

	SORT(rijec); //pozivanje funckije
}OBJASNJANJE ZA OVAJ ABECEDNI POSTUPAK(506-508 LINIJA KODA)*/

/*U varijabli "recenica" zapisan je tekst koji je potrebno analizirati. Napišite funkciju BRISI koja će
obrisati iz zadanog teksta znakovni niz(podniz). Ukoliko se zadani znakovni niz ponavlja više puta,
funkcija briše sva takva pojavljivanja. Kao rezultat funkcija vraća novi, preuređeni zapis.
Prototip funkcije:   string BRISI(string recenica, string trazeniNiz);


string BRISI(string recenica, string trazeniNiz) {

	int nadi = recenica.find(trazeniNiz);

	while (nadi >= 0) { // ovaj uvjet se ispunjava sve dok nadi ne dode do kraja trazene rijeci
		recenica.erase(nadi,trazeniNiz.length()); //obrisem sve dijelove recenice koje sadrze trazenu rijec(trazeniNiz)
		nadi = recenica.find(trazeniNiz); //zasto ovo ponavljati??????????
	}
	return recenica;
}
int main() {

	string recenica, trazeniNiz;

	cout << "Upisi recenicu :";
	getline(cin, recenica);

	cout << "Upisi dio recenice koji zelis izbrisati :";
	getline(cin, trazeniNiz);

	cout << BRISI(recenica,trazeniNiz); //pozivanje i ispisivanje funckije
	
}
*/
/*U tablici veličine 100 * 100 zapisani su cijeli brojevi.Napišite funkciju ODREDI koja će odredtiti
koji brojevi u tablici sadrže znamenku koja se traži.Kao rezultat funkcija vraća novi vektor u kojem
su zapisani brojevi iz tablice koji zadovoljavaju uvjet.Funkcija ima dva ulazna argumenta : tablicu s podacima
i broj koji označava traženu znamenku.Prototip funkcije :
vector<int> ODREDI(int tablica[100][100], int znamenka); 

vector<int> ODREDI(int tablica[2][2], int znamenka) {

	int brojac = 0;
	vector <int>OdgovarajuciBrojevi;
	int drugiOblikTablice;
	int brojevi;
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {

			drugiOblikTablice = tablica[i][j]; //trebamo dvije variable jer ce jedna prolaziti kroz brojeve i smanjivati ih dok ne dode do
			//broja koji zeli, dok ako program nade takvu znamenku nju moramo ispisati, ali s drugom varijablom(brojevi) koja pamti samo brojeve
			//koji se upisuju u visual studio
			brojevi = drugiOblikTablice;

			while (drugiOblikTablice != 0) {
				if (drugiOblikTablice % 10 == znamenka) {
					cout << brojevi << " , ";
					break;
					
				}
				else {
					drugiOblikTablice=drugiOblikTablice / 10;
				}
			}
		}
	}
	return OdgovarajuciBrojevi;
}

int main() {

	int tablica[2][2];
	int znamenka;
	vector<int>trazenibroj_vektor;


	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Upisi neke brojeve u tablicu :";
			cin >> tablica[i][j];
		}
	}

	cout << "Upisi znamenku koju zelis pretraziti iz tablice :";
	cin >> znamenka;

	trazenibroj_vektor = ODREDI(tablica, znamenka); //pozivanje funckije putem vektora, jer je sama "funckija" vector<int> ODREDI

}*/


/*U datotekama "kino.txt" zapisani su podaci o kazališnim predstavama.  U svakom redu datoteke
nalazi se zapisnao ime i prezime glumca, odvojeno razmakom. Napišite funkciju TRAZI
koja čita podatke iz datoteke te odredi  koliko glumaca u datoteci ima traženo ime. Funkcija na
zaslonu ispiše ime i prezime onih glumaca u čija imena su jednaka traženoj. Prototip funkcije:
vector<string>TRAZI(string trazenoIme);

vector<string>TRAZI(string trazenoIme) {


	ifstream datoteka;
	datoteka.open("kino.txt");

	string UpisImena;
	int brojac = 0;
	vector<string>bezveze;
	string ime;

	if (datoteka.is_open()) {

		while (getline(datoteka, UpisImena)) { //sve dok se datoteka zapisuje u STRING UpisImena (zato je takva struktura, s getline)
			
			ime = "";
			for (int i = 0; i < UpisImena.length(); i++) {
				if (UpisImena[i] != ' ') {
					ime = ime + UpisImena[i];
				}
				else {
					break;
				}
				if (ime == trazenoIme) {
					cout << UpisImena << " , ";
					bezveze.push_back(ime);
					brojac++;
				}
			}
		}
		datoteka.close();
	}
	if (brojac == 0) {
		cout << "Nema tog imena u datoteci! " << endl;
	}
	else {
		cout << endl; //estetika
		cout << "Broj takvih imena u datoteci :" << brojac << endl;
		return bezveze;
	}
}
int main() {


	ifstream datoteka;
	datoteka.open("kino.txt");

	string trazenoIme;

	if (datoteka.is_open()) {

		cout << "Upisi ime koje zelis pretraziti :";
		getline(cin, trazenoIme);
	}
	else {
		cerr << "Error!" << endl;
		exit(1);

	}
	TRAZI(trazenoIme); //Pozivanje funckije
}
*/


/*U matrici 10*10 zapisani su cijeli brojevi. Napišite funkciju NOVA_MATRICA koja će na
temelju te ulazne matrice formirati novu matricu veličine 10*10 u koju će upisati sumu znamenaka
svakog upisanog broja. Tako ao je u ulaznoj matrici na poziciji [3][3] upisan broj 123, funkcija
će kao rezultat izračunati sumu znamenaka koja u ovom primjeru iznosi 6 i taj će rezultat upisati u
novu matricu na istu poziciju [3][3]. Funkcija kao ulazne parametre ima dvije matrice.
Prototip funkcije: void NOVA_MATRICA (int ulaz[10][10],int nova[10][10]);

void NOVA_MATRICA(int ulaz[2][2], int nova[2][2]) {

	int brojevi;
	int trenutno;
	int zbrajanje=0;

	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {

			trenutno = ulaz[i][j];

			do {
				brojevi = trenutno % 10;
				trenutno = trenutno / 10;

				zbrajanje = zbrajanje + brojevi;


			} while (trenutno != 0);
			cout << "Zbroj znamenki svih upisanih brojeva (po redu) :" ;
			nova[i][j] = zbrajanje;   //upis sume znamenaka (varijabla zbrajanje) u novu matricu (nova)
			cout << zbrajanje<<endl;
			zbrajanje = 0; //resetiramo zbrajanje za druge brojeve
		}
	}
}

int main() {

	int ulaz[2][2];
	int nova[2][2];
	int novo;
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Upisi brojeve u tablicu :";
			cin >> ulaz[i][j];
		}
	}
	NOVA_MATRICA(ulaz,nova); //pozivanje funkcije
}*/


/*U tablici T dimenzije 20*20 uppisane su rečenice. Napiši funkciju PROVJERA koja će provjeriti koja
rečenica iz polja ima najviše riječi. Kao rezultat funkcija vraća tu pronađenu rečenicu.
Prototip funkcije: string provjera(string tablica[20][20]);

string provjera(string tablica[2][2]) {
	string privremenaRecenica;
	int brojacRijeci = 1;
	int max = 0; //maksimalnu vrijednost postavljamo na nulu kako bi svaka recenica koja ima bar jednu rijec preuzela vrijednost max
	int pokusaj = 0;
	string recenicaSNajviseRijeci;


	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {

			privremenaRecenica = tablica[i][j];
			for (int k = 0; k < privremenaRecenica.length(); k++) {
				if (privremenaRecenica[k] == ' ') {

					brojacRijeci++;
				}
				else {
					pokusaj++;
				}
				if (brojacRijeci > max) {
					max = brojacRijeci; // ide ovako, a ne obrnuto, jer varijabla max dobiva novu vrijednost, a to je brojacRijeci (tablica[i][j])
					recenicaSNajviseRijeci = privremenaRecenica;
				}
			}
			brojacRijeci = 1; //postavljanje brojacaRijeci na pocetnu vrijednost, kako bi mogao brojati rijeci na drugim rijecima (1)
		}
	}
	cout << "----------------" << endl; //estetika
	cout << "Najvisi broj rijeci ima recenica sa :" << max << " rijeci! " << endl;
	cout <<"A ta recenica je :" << recenicaSNajviseRijeci << endl;
	return privremenaRecenica;
}

int main() {


	string tablica[2][2];


	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Upisi recenice u tablicu :";
			getline(cin, tablica[i][j]);
		}
	}

	provjera(tablica); //pozivanje funckije
}*/


/*U datoteci su zapisani brojevi. Napišite funkciju PARNI_NEPARNI koja će brojeve
iz datoteke "ParniNeparni.txt" zapisati u novi vektor ali na ančin da parne brojeve zapiše
na početak vektora,a neparne brojeve na kraj vektora. Na taj način podaci u vektoru će
biti podijeljeni. Prototip funkcije:
vector<int> PARNI_NEPARNI();

vector<int> PARNI_NEPARNI() {

	vector<int>NoviVektor;
	int parni = 0;
	int neparni = 0;
	ifstream datoteka;
	datoteka.open("ParniNeparni.txt");
	int VarijablaZaBrojeveIzDatoteke=0;

	if (datoteka.is_open()) {

		while (datoteka >> VarijablaZaBrojeveIzDatoteke) {

			if (VarijablaZaBrojeveIzDatoteke % 2 == 0) {
				parni++;
				NoviVektor.insert(NoviVektor.begin(), VarijablaZaBrojeveIzDatoteke);
				
			}

			else  {
				neparni++;
				NoviVektor.push_back(VarijablaZaBrojeveIzDatoteke);
			}
		}
		
	}
	
	for (int i = 0; i<NoviVektor.size(); i++) { //for petlja za ispisivanje brojeva u program
	}
	cout << endl;
	cout << "----------------------------------" << endl;
	cout << "Broj parnih brojeva :" << parni << endl;
	cout << "Broj neparnih brojeva :" << neparni << endl;
	
	return NoviVektor;
}

int main() {

	PARNI_NEPARNI(); //Pozivanje funckije
}
*/


/*U datoteci "stanovi.txt" nalaze se zapisane cijene stanova izražene u kunama.
Podaci su zapisani na na?in da je prvo zapisana cijena,a u sljede??em redu adresa stana.
Cijene su tipa integer. Napišite funkciju STAN_CIJENA koja ?e odrediti sve stanove
?ije cijene su u zadanom rasponu. Funkcija adrese stanova zapisuje u novi vektor koji vra?a kao rezultat.
Prototip funkcije: vector<string> GRAD_CIJENA(int cijenaOD, int cijenaDO);


vector<string> GRAD_CIJENA(int cijenaOD, int cijenaDO) {


	ifstream datoteka;
	datoteka.open("Stanovi.txt");

	string novaVarijabla;
	string adrese;
	int trenutniBroj;
	int brojac = 0;
	int cijena = 0;
	vector<string>Vektoradresa;
	

	cout << "Stanovi koji odgovaraju vasem budzetu :" << endl;
	cout << "---------------------------------" << endl;

	if (datoteka.is_open()) {

		while (getline(datoteka, novaVarijabla)) //u while petlji postavim uvjet koj bude radio tako dugo dok se iz datoteke iscitavaju brojevi u trenutnibroj
		{
			string space;
			istringstream text_stream(novaVarijabla);
			text_stream >> cijena;
			getline(text_stream, space, ' '); //odvajanje broja cijene od adrese, odnosno dok ne dode do razmaka
			
			getline(text_stream, adrese); //odvajanje lokacije stanova od cijene


				if (cijena>=cijenaOD && cijena<=cijenaDO) //provjeram uvjet koji gleda je li trenutni broj veci od pocetnog i manji od zadnjeg broja u rasponu
				{
					cout << adrese<<endl;
					Vektoradresa.push_back(novaVarijabla);
					brojac++; //ako je uvjet zadovoljen brojac povecavam za jedan
					
				}
				
			}
			
		}
	if(brojac != 0) {
		cout << endl; //estetika
		cout << "Broj stanova koji su za vas :" << brojac << endl;
	}
	else {
		cout << "Nijedan stan ne odgovara vasem budzetu! " << endl;
	}

	return Vektoradresa; //vracamo vrijednost vektora
	}



	
int main() {

	int cijenaOD, cijenaDO;

	cout << "Upisi cijenu stana koja ti odgovara :";
	cin >> cijenaOD;

	cout << "Upisi do koje cijene ti odgovara :";
	cin >> cijenaDO;

	GRAD_CIJENA(cijenaOD, cijenaDO); //pozivanje funckije
}

*/



/*U datoteci "KolicinaBrojeva.txt" upisani su dvoznamenkasti cijeli brojevi.
SVaki broj nalazi se zapisan u zasebnom redu u datoteci. Napisite funkciju
RASPON koja ce odrediti koliko brojeva iz datoteke, njihove vrijednosti, se
nalaze u zadanom rasponu brojeva.
int raspon(int broj_od, int broj_do);


int raspon(int broj_od, int broj_do) {

	ifstream datoteka;
	datoteka.open("KolicinaBrojeva.txt");

	int brojevi;
	int brojac = 0;


	while (!datoteka.eof()) {

		datoteka >> brojevi;


		if (brojevi > broj_od && brojevi < broj_do) { //ona moja sintaksa ne radi (broj_od <=brojevi<=broj_do)
			cout << brojevi << " , ";
			brojac++;
		}
	}
	cout << endl; //estetika
	cout << "Broj brojeva u tom spektru :" << brojac << endl;
	return 0;
}

int main() {

	int broj_od,broj_do;

	cout << "Upisi od granicu :";
	cin >> broj_od;

	cout << "Upisi granicu do :";
	cin >> broj_do;

	raspon(broj_od, broj_do); //pozivanje funckije
}*/

/*Napišite funkciju BRISI_NAJVECI koja u polju cijelih brojeva briše najveći broj,
na njegovo mjesto zapisuje broj 0. Funkcija ima argument: polje brojeva. Kao rezultat
funkcija vraća oznaku indeksa pozicije broja koji je obrisan. Prototip funkcije:int BRISI_NAJVECI(int polje[50])

int BRISI_NAJVECI(int polje[4]) {

	int trenutniBroj;
	int max = 0; //postavljanjamo vrijednost max na nula kako bi svaki broj upisani (samo da je veci od nula) preuzeo vrijednost max
	string nes;
	int indeks;
	for (int i = 0; i < 4; i++) {
		trenutniBroj = polje[i];
		cout << polje[i] << " , ";
	
		if (trenutniBroj > max) {
				max = trenutniBroj;
				indeks = i;
		}
	}
	cout << endl; //estetika
	cout << "--------------------" << endl;
	cout << "Najveci broj je :" << max << endl;
	cout << "--------------------" << endl;

	for (int i = 0; i < 4; i++) {
		max = 0; //inicijalizirali smo da jje max nula, a s obzirom da smo indeks kreirali kada je vec odreden max broj(976 linija)
		// tada polje na indeksu (odnosno uzima se maksimalni broj koji se odredio u zad dobiva vrijednost 0[987 linija]
		//nakon toga se ponovno cout-a polje kao i u 972. liniji koda
		polje[indeks] = max;
		cout << polje[i] << " , ";
	}
	return 0;
}

int main() {

	int polje[4];


	for (int i = 0; i < 4; i++) {
		cout << "Upisi brojeve u polje (IZBRISAT CE SE NAJVECI U PREUREĐENOM NIZU) :";
		cin >> polje[i];
	}
	BRISI_NAJVECI(polje); //pozivanje funckije
}*/

/* U polju 3 x 3 zapisana su imena osoba. Napišite funkciju IMENA koja će odrediti  koliko upisanih imena završava sa slovom „a“.
Funkcija kao rezultat vraća broj imena koja zadovoljavaju uvjet. Prototip funkcije:
int IMENA( string [ ] [ ] polje);

int IMENA(string polje [2][2]) {

	int brojac = 0;
	
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			string TrenutnoIme = polje[i][j];

			char zadnjeSlovoUImenu = TrenutnoIme.back();

				if (zadnjeSlovoUImenu == 'a') {
					brojac++;
				}
			
		}
	}

	cout << "Broj imena sa zadnjim slovom 'a' u polju je : " << brojac << endl;
	return 0;
}

int main() {

	string polje[2][2];


	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Upisi imena u polje :";
			getline(cin, polje[i][j]);
		}
	}
	IMENA(polje); //pozivanje funckije 
}*/

/*U vektoru su zapisana imena gradova. Napišite funkciju BRISI koji će obrisati sva imena koja su duža
od zadane dužine. Funkcija ima dva parametra: vektor s podacima i zadanu duljinu. Kao rezultat
funkcija vraća vektor s imenima gradova koja su ostala nakon brisanja.
Prototip funkcije:
vector <string>  BRISI(vector <string> vec, int duljina);


vector <string> BRISI(vector <string> vec, int duljina) {

	string trenutniGrad;
	int indeks;
	vector<string>gotoviNiz;
	int bilokaj;
	for (int i = 0; i < vec.size(); i++) {
		trenutniGrad = vec[i]; //dodijeljujemo vrijednost gradova i zapisujemo u varijablu tipa string
		
			bilokaj = trenutniGrad.length();  //

		if (bilokaj <= duljina) { //ako je duljina slova gradova jednaka ili manja od unesene, ispises te gradove
			gotoviNiz.push_back(trenutniGrad); //i push-am ih u vektoru, koji mi kasnije sluzi za return
		}
		
	}
	for (int i = 0; i < gotoviNiz.size(); i++) { //ispis podataka iz vektora
		cout << gotoviNiz[i] << " . ";
	}
	return gotoviNiz;
}

int main() {


	vector <string> vec;
	int duljina;
	string gradovi;

	for (int i = 0; i < 3; i++) {
		cout << "Upisi imena gradova :";
		getline(cin, gradovi);
		vec.push_back(gradovi);
	}

	cout << "Upisi duljinu slova imena gradova koje zelis limitirati :";
	cin >> duljina;

	BRISI(vec,duljina); //pozivanje funckije
}

*/

//DRUGI NACIN OVOG ZAD

/*
vector <string> BRISI(vector <string> vec, int duljina) {

	string trenutniGrad;
	vector<string>gotoviNiz;
	int bilokaj;


	for (int i = 0; i < vec.size(); i++) {
		trenutniGrad = vec[i]; //uzimamo neki grad iz vektora

		bilokaj = trenutniGrad.length();  //dodijeljujemo varijabli tipa string duzinu pojedinog grada

		if (bilokaj > duljina) { //ako je duljina nekog grada veca od dozvoljene, odnosno koje je korisnik odredio, ona se brise iz polja

			vec.erase(vec.begin() + i);//naredba za brisanje vektora na odredenom indeksu
			//Since std::vec.begin() marks the start of container and if we want to delete the ith element in our vector
			gotoviNiz.push_back(trenutniGrad);
		}
	}
	for (int i = 0; i < vec.size(); i++) { //ispis niza koji zadovoljava uvijete
		cout << vec[i] << " . ";
	}
	return gotoviNiz;
}

int main() {


	vector <string> vec;
	int duljina;
	string gradovi;
	                               
	for (int i = 0; i < 3; i++) {
		cout << "Upisi imena gradova :";
		getline(cin, gradovi);
		vec.push_back(gradovi);
	}

	cout << "Upisi duljinu slova imena gradova koje zelis limitirati :";
	cin >> duljina;

	BRISI(vec, duljina); //pozivanje funckije
}
*/

/*Napišite funkciju NIZ koja upisuje u 1D polje dužine 3 elemenata imena osoba. 
Upis se izvršava tako dugo dok nisu upisana svih 10 imena ili je upisano ime koje već postoji. 
U tom slučaju prekida se upis i  funkcija vraća broj uspješno upisanih imena. Upis neka je realiziran obavezno pomoću do – while naredbe. 
Prototip funkcije: 
int NIZ (string polje[3]);


int NIZ(string polje[3]) {

	bool ImeJeVecUpisano = false;
	int brojacImena=0;
	int pokusaj = 0;
	string trenutnoIme;


	do {
		for (int i = 0; i < 3; i++) {
			cout <<"Upisana su imena :"<< polje[i] << " , ";
			break;
			brojacImena++;

			if (polje[i] != polje[i]) {
				brojacImena++;
			}
			else {
				break;
			}
	    }
		
		
	} while (brojacImena < 3); //ogranicio sam unos zbog for petlje

	cout << "Upisano je " << brojacImena << " imena" << endl;
	return 0;
}

int main() {
	string polje[3];


	for (int i = 0; i < 3; i++) {

		cout << "Upisi imena osobe :";
		getline(cin, polje[i]);
	}

	NIZ(polje); //pozivanje funckije
}*/

/* Napišite funkciju RECENICA koja će odrediti riječi unutar zadane rečenice i zapisat riječi u izlaznu datoteku „izlaz.txt“.
Funkcija kao rezultat vraća broj koji označava broj upisanih riječi. Prototip funkcije:
int RECENICA( string data);


int RECENICA(string data) {

	ofstream datoteka;
	datoteka.open("izlaz.txt");

	int brojacRijeci = 1;

	if (datoteka.is_open()) {

		datoteka << data; //zapisujemo recenicu iz visual-a u datoteku

		for (int i = 0; i < data.length(); i++) {

			if (data[i] == ' ') {
				brojacRijeci++;
				
			}

		}
		cout << "Broj rijeci iz recenice je : ";
		cout << brojacRijeci; //upis broja u visual studio
		datoteka<<" : " << brojacRijeci; //upis broja u datoteku, ova dvotocka je kao estetika da ljepse izgleda upis u datoteku
	}

	else {
		cerr << "Error" << endl;
		exit(1);
	}
}
int main() {

	string data;

	cout << "Upisi recenicu :";
	getline(cin, data);

	RECENICA(data); //pozivanje funckije
}
*/

/*U vektoru su zapisani cijeli brojevi. Napišite funkciju MIN_MAX koji će odrediti najveći i najmanji upisani broj.
Minimalni broj će premjestiti iz vektora na njegov početak, a najveći broj će premjestiti na kraj vektora.
Funkcija vraća tako izmijenjen vektor. Prototip funkcije:
vector <int> MIN_MAX(vector <int> VEC);


vector <int> MIN_MAX(vector <int> VEC) {

	int max = 0;
	int min =VEC[0];
	int varijabla;
	int pokusaj = 0;
	vector<int> brojevi;

	for (int i = 0; i < VEC.size(); i++) {

		varijabla = VEC[i]; //Dodavanje vrijednosti varijabli tipa int

		if (varijabla > max) {
			max = varijabla;
			brojevi.push_back(max); //najveći broj premještamo na kraj vektora
		}
		else {
			pokusaj++;
		}
		if (varijabla != 0) {
			if (VEC[i] < max) {
				min = varijabla;
				brojevi.insert(brojevi.begin(), min); //postavljanje min vrijednosti na kraj vektora
			}
		}
	}

	cout << "-------------" << endl;
	cout << "Max broj je :" << max << endl;
	cout << "Min broj je :" << min << endl;

	return brojevi; //vracanje vektora
}

int main() {

	int unos;
	vector <int> VEC;

	do {

		cout << "Upisi brojeve u niz :";
		cin >> unos;
		VEC.push_back(unos);
		
	} while (unos != 0);

	MIN_MAX(VEC); //Pozivanje funckije
}
*/

/* U datoteci su zapisani realni brojevi.Napišite funkciju DATOTEKA koja će pročitati brojeve iz datoteke
i zapisati u vektor samo one koji su veći od broja PI.
Nakon upisa neka funkcija vrati iznos zbroja upisanih brojeva.Prototip funkcije : float DATOTEKA(string nazivDatoteke); 

float DATOTEKA() {

	ifstream datoteka;
	datoteka.open("BrojeviVeciOdPi.txt");

	float brojevi;
	int trenutniBroj;
	int suma=0;
	int brojac = 0;
	vector<float> nes;

	if (datoteka.is_open()) {

		while (datoteka >> brojevi) {
			if (brojevi > 3.14) {
				nes.push_back(brojevi);
				suma = suma + brojevi;
				brojac++;
			}

		}	
		for (int i = 0; i < nes.size(); i++) { //ispis brojeva zapisanih u vektor (samo oni veci od PI vrijednosti)
			cout << nes[i]<<" , ";
		}
	}
	cout << endl;

	cout << "Suma svih brojeva vecih od PI je :" << suma << endl;
	cout << "Broj brojeva iz datoteke koji je veci od PI je :" << brojac << endl;
	return 0;
}

int main() {

	DATOTEKA(); //POZIVANJE FUNCKIJE
}*/

/*Napišite funkciju BROJ koji će u vektor zapisivati realni broj na način da ako je broj veći od 5,00 i manji od 8,00,
funkcija broj zapiše na početak vektora, u suprotnom na kraj. Funkcija je zadana prototipom:
void BROJ(vector <float> vec, float broj);


void BROJ(vector <float> vec, float broj) {

	vector<float>novi;

	for (int i = 0; i < vec.size(); i++) {

		int trenutniBroj = vec[i];

		if (vec[i] != 0) {

			if (trenutniBroj > 5 && trenutniBroj < 8) {
				novi.insert(novi.begin(), trenutniBroj);
			}
			else {
				novi.push_back(trenutniBroj);
			}
		}
	}
	cout << "Rezultat :";
	for (int i = 0; i < novi.size(); i++) {
		cout << novi[i] << " , ";
	}
}

int main() {

	float broj;
	vector<float> vec;

	for (int i = 0; i < 4; i++) {
		cout << "Upisi brojeve :";
		cin >> broj;
		vec.push_back(broj);
	}
	BROJ(vec,broj); //pozivanje funckije
}

*/


/*U 1D polju nalaze se upisani cijeli brojevi. Napišite funkciju OKRENI koja će zamijeniti mjesta svim
elementima polja na način da se dobije zrcalna slika. Funkcija ima jedan argument proslijeđen prema
referenci. Prototip funkcije:
void OKRENI (int &polje[4]); //array of referece is not allowed-error description


void OKRENI(int polje[4]) {
	cout << "Preokrenuti niz glasi :";

	for (int i = 4; i >= 0; i--) {
		cout << polje[i] << " , ";
	}
}

int main() {

	int polje[4];


	for (int i = 0; i < 4; i++) {
		cout << "Upisi brojeve u polje (kao rezultat oni ce se okrenuti) :";
		cin >> polje[i];
	}

	OKRENI(polje); //pozivanje funkcije
}
*/

/*Napišite funkciju UPIS koja će zahtijevati od korisnika da upiše cijeli broj. Ukoliko je upisani broj
višekratnik broja 5 taj broj funkcija upiše u datoteku „brojevi5.txt“. Svaki upisani broj mora se nalaziti u
svojem redu datoteke. Korisnik upisuje brojeve tako dugo dok ne upiše broj 100. Nakon toga funkcija
završava s upisom i kao rezultat vraća broj koji označava koliko je brojeva upisano u datoteku.
Prototip funkcije:
int UPIS();

int UPIS() {

	ofstream datoteka;
	datoteka.open("brojevi5.txt");
	int brojevi;
	if (datoteka.is_open()) {

		do {

			cout << "Upisi cijeli broj :";
			cin >> brojevi;

			if (brojevi % 5 == 0) {
				datoteka<<brojevi;
				datoteka << endl; //upis svakog broja u novi red
			}

		} while (brojevi != 100);

	}
	else {
		cerr << "Erorr";
		exit(1);
	}
}

int main() {

	UPIS();
}

*/

/*U datoteci su zapisani cijeli brojevi, svi brojevi nalaze se  zapisani u jednom redu odvojeni točkom
zarez (;). Napišite funkciju VISEKRATNIK koja će pročitati brojeve iz datoteke i u vektor zapiše samo
one brojeve koji su višekratnici broja 3. Kao rezultat funkcija vraća broj upisanih brojeva u vektor.
Prototip funkcije:
int VISEKRATNI(string nazivDatoteke);


int VISEKRATNI() {

	ifstream datoteka;
	datoteka.open("Visekratnicitrojke.txt");

	string brojevi;
	int novaVarijabla=0;
	int trenutniBroj;
	int brojac = 0;
	if (datoteka.is_open()) {

		getline(datoteka, brojevi); //ZAPISUJEMO PODATKE IZ DATOTEKE U VARIJABLU TIPA STRING
		for (int i = 0; i < brojevi.length(); i++) {
			trenutniBroj = brojevi[i];
		}

		while (brojevi!= ";") {
			
			novaVarijabla = novaVarijabla + trenutniBroj;

			if (brojac < brojevi.length()) {
				if (novaVarijabla % 3 == 0) {
					cout << novaVarijabla << " , ";
					brojac++;
					
				}
			}
		}
		cout << endl; //estetika
		cout << "Broj takvih brojeva je :" << brojac << endl;
	}
	else {
		cerr << "Error" << endl;
		exit(1);
	}
	return 0;
}

int main() {

	VISEKRATNI(); //POZIVANJE FUNCKIJE
}
 NE RADI
*/

/*U polju 3 x 3 zapisani su cijeli brojevi. Napišite funkciju POLJE koja će odrediti  koliko upisanih brojeva
u polju ima drugu znamenku jednaku broju 3. Funkcija vraća rezultat i ima sljedeći prototip:

int POLJE( int [] [] polje);
 (pretpostavljam int POLJE( int polje [] []);)

Na primjer:
Ako su u polju zapisani brojevi: 1, 4, 34, 2, 55, 135, 3, 8, 10
Rezultat: 2 broja


int POLJE(int polje[2][2]) {

	int trenutniBroj;
	int prvaznamenka,drugaznamenka;
	int brojac = 0;
	int ukupno;
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {

			trenutniBroj = polje[i][j];
			do {

				drugaznamenka =trenutniBroj % 10;
				trenutniBroj = trenutniBroj / 10;
				
			} while (trenutniBroj != 0);

					if (drugaznamenka == 3) {
						cout << trenutniBroj << " , ";
						brojac++;
					}

		}
	}
	if (brojac == 0) {
		cout << "Nema brojeva kojim je druga znamenka 3!" << endl;
	}
	cout << endl; //estetika
	cout << "-----------------" << endl;
	cout << "Broj takvih brojeva je :" << brojac << endl;
	return 0;
}

int main() {

	int polje[2][2];

	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Unesi brojeve u polje :";
			cin >> polje[i][j];
		}
	}
	POLJE(polje);//poziv funckije
}
NE RADI
*/

/* Napišite funkciju VEKTOR koji će u vektor zapisivati imena studenata na način da ako u imenu
studenta ima slova „M“ i „N“ ime zapisuje na početak vektora, u suprotnom na kraj.Funkcija je zadana
prototipom :
void VEKTOR(string imeStudenta);


void VEKTOR(string imeStudenta[3]) {

	vector<string>imena;
	string trenutnoIme;

	for (int i = 0; i < 3; i++) {
		trenutnoIme = imeStudenta[i];
	
		if (trenutnoIme[0] == 'M' || trenutnoIme[0] == 'N') {

			imena.insert(imena.begin(), imeStudenta[i]);
		}
		else {
			imena.push_back(imeStudenta[i]);
		}
	}
	for (int i = 0; i < imena.size(); i++) { //ispis vektora
		cout << imena[i] << " , ";
	}
}

int main() {

	string imeStudenta[3];

	for (int i = 0; i < 3; i++) {
		cout << "Upisi ime studenta :";
		getline(cin, imeStudenta[i]);
	}
	
	VEKTOR(imeStudenta); //pozivanje funckije
}
*/


/*U tablici T dimenzije 20*20 upisane su rečenice. Napisi funckiju PROVJERA koja ce provjeriti koja 
recenica u polju ima najvise rijeci.Kao rezultat funckija vraca tu pronadenu recenicu
string PROVJERA(string tablica[20][20]);


string PROVJERA(string tablica[2][2]){

	string maxRecenica;
	int max = 0;
	int brojacRijeci = 1;
	int pokusaj = 0;
	string trenutnaRecenica;
	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {

			 trenutnaRecenica = tablica[i][j];
			for (int k = 0; k < trenutnaRecenica.length(); k++) {

				if (trenutnaRecenica[k] == ' ') {

					brojacRijeci++;
				}
				else {
					pokusaj++;
				}
				if (brojacRijeci > max) {
					max = brojacRijeci;
					maxRecenica = trenutnaRecenica;
				}
			}
			brojacRijeci = 1; //ZBOG OVOG SAM RJESAVAO ZADATAK 2H!!!!!!!!!!!!!!!!!!!!!!!
		}
	}
	cout << "-------------------" << endl;
	cout << "Recenica s najvecim brojem rijeci je :" << maxRecenica << endl;
	cout << "Broj rijeci koja te recenica ime je :" <<max<< endl;

	return 0;
}

int main() {

	string tablica[2][2];

	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Upisi recenicu :";
			getline(cin, tablica[i][j]);
		}
	}

	PROVJERA(tablica); //pozivanje funckije
}

*/

/* Napišite funkciju UPIS_DATOTEKA zapisuje u datoteku "recenicaa.txt" re?enice koje upisuje korisnik.
U datoteku se zapisuju samo re?enice koje se sastoje od to?no zadanog broja rije?i. Ukoliko se re?enica ne sastoji od
zadanog broja rije?i, takva re?enica se ne upisuje u datoteku. Upis završava kada korisnik tri(3) puta pogrešno upiše re?enicu.
Prototip funkcije za upis: int UPIS_DATOTEKA(int brojRijeci);


int UPIS_DATOTEKA(int brojRijeci) {

	int brojacGreski = 0; //moze ih biti max 3
	
	string recenica;
	ofstream datoteka;
	datoteka.open("recenicaa.txt");

	if (datoteka.is_open()) {
		while (!datoteka.eof()) {

			int brojacRijeciURecenici = 1; //mora biti tu deklarirano jer ne radi dobro program

			cout << "Upisi recenicu :";
			cin.ignore(); //da ignora prvi upis
			getline(cin, recenica);

			for (int i = 0; i < recenica.length(); i++) {
				if (recenica[i] == ' ') {
					brojacRijeciURecenici++;
				}
			}
				if (brojRijeci == brojacRijeciURecenici) {
					datoteka << recenica << endl; //upis recenice u datoteku, ukoliko ispunjava uvjet
				}
				else {
					brojacGreski++;
					cout << "Greska broj :" << brojacGreski << endl;
					if (brojacGreski == 3) {
						break;
					}
				}
		}	
	}
		cout << "------------" << endl;
		cout << "Spremanje u datoteku je zavrseno!" << endl;

		return 0;
}
	


int main() {

	int brojRijeci;

	cout << "Upisi broj rijeci koji zelis ograniciti :";
	cin >> brojRijeci;

	UPIS_DATOTEKA(brojRijeci); //pozivanje funckije
}
*/

/* U dva vektora zapisani su brojevi. Napišite funkciju FORMIRAJ koja će formirati novu datoteku "brojevi.txt". Funkcija uspoređuje međusobno brojeve koji se nalaze u vektorima te u datoteku zapiše uvijek onaj broj elementa vektora koji je veći. Protorip funkcije:
void FORMIRAJ(vector<int>vec1,vector<int>vec2);
PR:
vektor1: 2, 4, 20, 8
vektor2: 8, 12, 4, 3
Datoteka "brojevi.txt" : 8, 12, 20, 8

void FORMIRAJ(vector<int>vec1, vector<int>vec2) {

	int trenutniBroj1, trenutniBroj2;
	ofstream datoteka;
	datoteka.open("VeciBrojevi.txt");

	if (datoteka.is_open()) {
		cout << "Konacno rjesenje (samo veci brojevi) :"; 
		for (int i = 0; i < vec1.size() && i < vec2.size(); i++) {
				trenutniBroj1 = vec1[i];
				trenutniBroj2 = vec2[i];
				
				if (trenutniBroj1 > trenutniBroj2) {
					datoteka << trenutniBroj1 << " , ";
					cout<< trenutniBroj1 << " , ";//ispis brojeva u visual studio
				}

				else {
					datoteka << trenutniBroj2 << " , ";
					cout << trenutniBroj2 << " , "; //ispis brojeva u visual studio
				}
		}
		cout << endl; //estetika
		cout << "UNOS U DATOTEKU JE ZAVRSEN!" << endl;
	}
	else {
		cout << "Error" << endl;
		exit(1);
	}
}


int main() {
	vector<int>vec1;
	vector<int>vec2;
	int vektor1, vektor2;


	for (int i = 0; i < 3; i++) {
		cout << "Unesi brojeve u prvi vektor :";
		cin >> vektor1;
		vec1.push_back(vektor1); //upisivanje brojeva u vektor
	}
	for (int i = 0; i < 3; i++) {
		cout << "Unesi brojeve u drugi vektor :";
		cin >> vektor2;
		vec2.push_back(vektor2); //upisivanje brojeva u vektor
	}

	FORMIRAJ(vec1, vec2); //pozivanje funckije
}
*/

/*U tablici veličine 100*100 zapisani su cijeli brojevi. Napišite funkciju ODREDI koja će odredtiti
koji brojevi u tablici sadrže znamenku koja se traži. Kao rezultat funkcija vraća novi vektor u kojem
su zapisani brojevi iz tablice koji zadovoljavaju uvjet. Funkcija ima dva ulazna argumenta: tablicu s podacima
i broj koji označava traženu znamenku. Prototip funkcije:
vector<int> ODREDI(int tablica[100][100], int znamenka);

vector<int> ODREDI(int tablica[2][2], int znamenka) {

	vector<int>NoviVektor;
	int brojac = 0;
	int trenutniBroj;
	string brojkaString;

	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			
			trenutniBroj = tablica[i][j];

			brojkaString = to_string(trenutniBroj);

			for (int k = 0; k < brojkaString.length(); k++) {
				if (brojkaString[k] == znamenka) {
					NoviVektor.push_back(trenutniBroj);
					brojac++;
				}
			}
		}
	}
	for (int v = 0; v < NoviVektor.size(); v++) { //ispisivanje podataka iz vektora u visual studio
		cout << NoviVektor[v] << " , ";
	}
	cout << endl; //estetika
	cout << "Broj takvih brojeva :" << brojac << endl;
	return NoviVektor;
}
int main() {

	int tablica[2][2];
	int znamenka;

	for (int i = 0; i < 2; i++) {
		for (int j = 0; j < 2; j++) {
			cout << "Upisi brojeve u tablicu :";
			cin >> tablica[i][j];
		}
    }
	cout << "Upisi znamenku koju zelis pretraziti :";
	cin >> znamenka;

	ODREDI(tablica, znamenka); //pozivanje funckije
}*/

/*U datotekama "kino.txt" zapisani su podaci o kazališnim predstavama.  U svakom redu datoteke
nalazi se zapisnao ime i prezime glumca, odvojeno razmakom. Napišite funkciju TRAZI
koja čita podatke iz datoteke te odredi  koliko glumaca u datoteci ima traženo ime. Funkcija na
zaslonu ispiše ime i prezime onih glumaca u čija imena su jednaka traženoj. Prototip funkcije:
vector<string>TRAZI(string trazenoIme);

vector<string>TRAZI(string trazenoIme) {

	ifstream datoteka;
	datoteka.open("KazalisnaPredstava.txt");
	string upisGlumaca;
	string ime;
	int brojac = 0;

	if (datoteka.is_open()) {

		while (getline(datoteka ,upisGlumaca)) {
			ime = "";
			for (int i = 0; i < upisGlumaca.length(); i++) {
				if (upisGlumaca[i] != ' ') {
					ime = ime + upisGlumaca[i];
				}
				else { //da ne ispisuje dva puta jedno ime
					break;
				}
				if (ime == trazenoIme) {
					cout << upisGlumaca << " , ";
					brojac++;
				}
			}
		}
		cout << endl; //estetika
		cout << "Broj takvih imena u datotteci :" << brojac << endl;

		if (brojac == 0) {
			cout << "Nema tkavih imena u datoteci!" << endl;
		}
	}
	else {
		cerr << "Error!" << endl;
		exit(1);
	}

}
int main() {
	
	string trazenoIme;

	cout << "Upisi trazeno ime koje zelis pretraziti iz datoteke :";
	getline(cin, trazenoIme);

	TRAZI(trazenoIme); //pozivanje funckije
	
}*/

/*U vektoru su zapisana imena gradova. Napišite funkciju BRISI koji će obrisati sva imena koja su duža
od zadane dužine. Funkcija ima dva parametra: vektor s podacima i zadanu duljinu. Kao rezultat
funkcija vraća vektor s imenima gradova koja su ostala nakon brisanja.
Prototip funkcije:
vector <string>  BRISI(vector <string> vec, int duljina);

vector <string> BRISI(vector <string> vec, int duljina) {

	vector<string>VektorZaGradove;
	string grad;
	int duzinaOdredenogGrada;
	int brojac = 0;
	int pokusaj = 0;

	for (int i = 0; i < vec.size(); i++) {
		grad = vec[i];

		duzinaOdredenogGrada = grad.length();

		if (duzinaOdredenogGrada > duljina) {
			vec.erase(vec.begin() + i);
		}
	}

	cout << "Rjesenje :";
	for (int i = 0; i < vec.size(); i++) {
		cout << vec[i] << " , ";
	}

	return VektorZaGradove;
}
int main() {

	string gradovi;
	vector<string>vec;
	int duljina;

	for (int i = 0; i < 3; i++) {
		cout << "Unesi gradove u vektor :";
		getline(cin, gradovi);
		vec.push_back(gradovi);

	}
	cout << "Unesi duljinu rijeci koju zelis limitirati :";
	cin >> duljina;

	BRISI(vec, duljina); //pozivanje funckije
}

*/

/*Napisati program koji od korisnika zahtjeva proizvoljni upis brojeva n, te odreduje koliko imena pocinje sa proizvoljnim slovima
int podaci(vector<string>imena, char c); prototip */


int podaci(vector<string>imena, char c) {

	int brojac = 0;
	string trenutnoIme;

	for (int i = 0; i < imena.size(); i++) {
		trenutnoIme = imena[i]; //upis imena iz vektora u varijablu tipa string

		if (trenutnoIme[0] == c) {
			brojac++;
		}
	}
	cout << "--------------" << endl; //estetika
	if (brojac != 0) {
		cout << "Broj imena koja pocinju sa trazenim znakom :" << brojac << endl;
	}
	else {
		cout << "U nizu ne postoji ime s tim pocetnim znakom!" << endl;
	}
	return brojac;
}
int main() {
	
	int brojevi;
	string ime;
	vector<string>imena;
	char trazenaSlova;

	cout << "Unesi koliko imena zelis unesti :";
	cin >> brojevi;

	cout << "Unesi trazenu rijec koju zelis pretraziti :";
	cin >> trazenaSlova;

	cout << "Unesi imena u vektor :";
	for (int i = 0; i <= brojevi; i++) {
		getline(cin, ime);
		imena.push_back(ime); //upisivanje imena iz varijable tipa string u vektor
	}

	podaci(imena, trazenaSlova); //pozivanje funckije
}
