# personaldata.cpp
#include "personaldata.h"

///Constructor base
PersonalData::PersonalData() {
    tel = "";
    email = "";
    status = "";
    cont = -1;
    }

Name PersonalData::getName() {
    return name;
    }

Address PersonalData::getAddress() {
    return address;
    }

std::string PersonalData::getTelphone() {
    return tel;
    }

std::string PersonalData::getEmail() {
    return email;
    }

std::string PersonalData::getStatus() {
    return status;
    }

std::string PersonalData::getCurp() {
    return curp;
    }

void PersonalData::setName(Name& n) {
    name = n;
    }

void PersonalData::setAddress(Address& a) {
    address = a;
    }

void PersonalData::setTelphone(std::string& t) {
    tel = t;
    }

void PersonalData::setEmail(std::string& e) {
    email = e;
    }

void PersonalData::setStatus(std::string& s) {
    status = s;
    }

void PersonalData::setCurp(std::string& c){
    curp = c;
    }

std::string PersonalData::toStringData(){
    std::string result;

    result += "Nombre: ";
    result += name.toString();
    result += " Curp: ";
    result += curp;
    result += " Direccion: ";
    result += address.toString();
    result += " Tel: ";
    result += tel;
    result += " Email: ";
    result += email;
    result += " Estado Civil: ";
    result += status;
    result += "\n";

    return result;
    }

/*** Dependientes Económicos ***/
bool PersonalData::isEmpty(){
    return cont == -1;
}

bool PersonalData::isFull(){
    return cont == 10;
    }

void PersonalData::insertData(int& p, Name& n, int& y) {
    if(isFull()) {
        throw ListException("Desbordamiento de datos\n\t\t***ERROR: EN INSERCION DE DATOS***");
        }
    if(p < -1 or p > cont ) {
        throw ListException("Desbordamiento de datos\n\t\t***ERROR: EN INSERCION DE DATOS***");
        }
    int i = cont;

    while(i > p) {
        family[i+1] = family[i];
        i--;
        }
    family[p+1].setName(n);
    family[p+1].setAge(y);
    cont = cont+1;
}

void PersonalData::deleteData(int& p) {
    if(isEmpty()){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN ELIMINACION DE DATOS***");
    }
    int i = p;
    while( i < cont ) {
        family[i] = family[i+1];
        i++;
        }
    cont--;
}

int PersonalData::getLastPos() {
    if(isEmpty()) {
        return -1;
        }
    return cont;
    }

int PersonalData::getFirstPos() {
    if(isEmpty()) {
        return -1;
        }
    return 0;
    }

EconomicDependent PersonalData::retrieve(const int& p) {
    if(isEmpty() or p < 0 or p > cont){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN BUSQUEDA DE DATOS***");
    }
    return family[p];
}

bool PersonalData::findData(Name& aux){
    for (int i = 0; i < cont; i++){
        if (aux.toString() == family[i].getName().toString()){
            return true;
        }
    }
    return false;
}

std::string PersonalData::toStringDependents() {
    std::string result;
    char years[5];
    int age;

    for(int i = 0; i <= cont; i++){
        result += "Nombre: ";
        result += family[i].getName().toString();

        age = family[i].getAge();
        result += " Edad: ";
        sprintf(years,"%02i",age);
        result += years;
        result += "\n";
    }
    return result;
}
