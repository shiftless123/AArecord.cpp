/*
 *  AArecord.cpp
 *
 *  COSC 052 Fall 2014
 *  Project #1
 *
 *  Due on: SEP 22, 2014
 *  Author: Henry Parrott
 *
 *
 *  In accordance with the class policies and Georgetown's
 *  Honor Code, I certify that, with the exception of the
 *  class resources and those items noted below, I have neither
 *  given nor received any assistance on this project.
 *
 *  References not otherwise commented within the program source code.
 *  Note that you should not mention any help from the TAs, the professor,
 *  or any code taken from the class textbooks.
 */

#include <string>
#include <ostream>
#include <istream>
#include <iostream>
#include <iomanip>

//Header Files
#include "DateTime.h"
#include "AArecord.h"

using std::string;
using std::ostream;
using std::istream;


AArecord::AArecord()
{
    eventID = "";
	city = "";
	state = "";
	country = "";
	investigationType = "";
	accidentNumber = "";
	Date eventDate (1993,3,24);
	countInjuredFatal = 1;
	countInjuredSerious = 1;
	countInjuredMinor = 1;
	countNonInjured = 1;
	registrationNumber = "";
	makeAndModel = "";

}

AArecord::AArecord(std::string ID, std::string city_name, std::string state_name,
                   std::string country_name, std::string iType, std::string aNumber,
         Date event_date, int fatal, int serious, int minor, int non,
         string rNumber, string MandM)
{
    ID = eventID;
    city_name = city;
    state_name = state;
    country_name = country;
    iType = investigationType;
    aNumber = accidentNumber;
    Date event_date = eventDate;
    fatal = countInjuredFatal;
    serious = countInjuredSerious;
    minor = countInjuredMinor;
    non = countNonInjured;
    rNumber = registrationNumber;
    MandM = makeAndModel;
    
}


string AArecord::getEventID() const
{
    return eventID;
}

string AArecord::getCity() const
{
    return city;
}

string AArecord::getState() const
{
    return state;
}

string AArecord::getCountry() const
{
    return country;
}

string AArecord::getInvestigationType() const
{
    return investigationType;
}

string AArecord::getAccidentNumber() const
{
    return accidentNumber;
}

Date AArecord::getEventDate() const
{
    return eventDate;
}

int AArecord::getCountInjuredFatal() const
{
    return countInjuredFatal;
}

int AArecord::getCountInjuredSerious() const
{
    return countInjuredSerious;
}

int AArecord::getCountInjuredMinor() const
{
    return countInjuredMinor;
}

int AArecord::getCountNonInjured() const
{
    return countNonInjured;
}

string AArecord::getRegistrationNumber() const
{
    return registrationNumber;
}

string AArecord::getMakeAndModel() const
{
    return makeAndModel;
}

ostream &operator <<(ostream& os, const AArecord & AAObj)
{
    // Prints an 'AAObj' Object in the same format as the input file
    os << std::left << std::setw(20)<< AAObj.eventID
    << AAObj.city
    << AAObj.state
    << AAObj.country
    << AAObj.investigationType
    << AAObj.accidentNumber
    << AAObj.eventDate
    << AAObj.countInjuredFatal
    << AAObj.countInjuredSerious
    << AAObj.countInjuredMinor
    << AAObj.countNonInjured
    << AAObj.registrationNumber
    << AAObj.makeAndModel;
    
    return os;
}

//Overloaded stream extration operator (AAObject class)
istream &operator >>(istream& is, AArecord& AAObj)
{
    is >> AAObj.eventID
	>> AAObj.city
	>> AAObj.state
	>> AAObj.country
	>> AAObj.investigationType
	>> AAObj.accidentNumber
	>> AAObj.eventDate
	>> AAObj.countInjuredFatal
	>> AAObj.countInjuredSerious
	>> AAObj.countInjuredMinor
	>> AAObj.countNonInjured
	>> AAObj.registrationNumber
	&& getline(is, AAObj.makeAndModel);
    //getline function is used to get all the info for make and model
    
	return is;
}
