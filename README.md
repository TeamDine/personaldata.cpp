# personaldata.cpp
///Implementacion de la clase para registro de datos personales
#include "personaldata.h"

///Constructor base
PersonalData::PersonalData() {
    tel = "";
    email = "";
    status = "";
    cont = 0;
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

int PersonalData::getCont(){
    return cont;
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

void PersonalData::setCont(int& c){
    cont = c;
    }
