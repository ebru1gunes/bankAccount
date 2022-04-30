# bankAccount
bankAccount işlemleri
#include <iostream>

using namespace std;


class bankAccount
{
private:
	float accountBalance;
	string personName, personSurname, personPhone;
public:
	bankAccount(string name, string surname, float balance = 0, string phoneNumber = " ");
	bankAccount(const bankAccount& oth);
	~bankAccount();
	bool controlNameSurname(string name_or_surname);
	bool controlphoneNumber(string phoneNumber);
	void displayProfile();
	void setPersonName(string name);
	void setPersonSurname(string Surname);
	void setPersonPhone(string phoneNumber);
	void setPersonBalance(float balance = 0);
	string getPersonName()
	{
		return personName;
	}
	string getPersonSurname()
	{
		return personSurname;
	}
	string getPersonPhone()
	{
		return personPhone;
	}
	float getPersonBalance()
	{
		return accountBalance;
	}


};


bool bankAccount::controlNameSurname( string name_or_surname)
{
	for (int i = 0; i < name_or_surname.length(); i++)
	{
		if (name_or_surname[i] >= 'A' && name_or_surname[i] <= 'Z' || name_or_surname[i] >= 'a' && name_or_surname[i] <= 'z')
		{
			return true;
		}

		else
		{
			return false;
		}

	}

}

bool bankAccount::controlphoneNumber(string phoneNumber)
{

	for (int i = 0; i < phoneNumber.length(); i++)
	{
		if (phoneNumber[i] >= '0' && phoneNumber[i] <= '9')
		{
			return true;
		}
		else
		{
			return false;
		}

	}
}

void bankAccount::setPersonName(string name)
{

	while (!controlNameSurname(name))
	{
		cout << " gecersiz name, Lutfen  name tekrar deneyiniz:" ;
		std::basic_istream::getline(cin, name);

    }

	personName = name;


}
void bankAccount::setPersonSurname(string Surname)
{

	while (!controlNameSurname(Surname))
	{
		cout << "gecersiz surname , lutfen tekrar surname giriniz:";

		std::basic_istream::getline(cin, Surname);


    }
	personSurname = Surname;

}
void bankAccount::setPersonPhone(string PhoneNumber)
{
	while (!controlphoneNumber(PhoneNumber))
	{
		cout << "gecersiz PhoneNumber , lutfen tekrar PhoneNumber giriniz:";
		std::basic_istream::getline(cin, PhoneNumber);
	}
	personPhone = PhoneNumber;


}

void bankAccount::setPersonBalance(float balance = 0)
{

	if (balance <= 0)
	{
		accountBalance = 0;

	}
	else
	{
		accountBalance = balance;
	}




}
bankAccount::bankAccount(string name, string surname, float balance = 0, string phoneNumber = " ")
{
	setPersonName(name);
	setPersonSurname(surname);
	setPersonPhone(phoneNumber);
	setPersonBalance(balance);


	cout << "constructor gerceklesti..";
}

bankAccount::~bankAccount()
{
	cout << "destructor gerceklesti..";

}
bankAccount::bankAccount(const bankAccount& oth)
{
	personName = oth.personName;
	personSurname = oth.personSurname;
	personPhone = oth.personPhone;
	accountBalance = oth.accountBalance;

	cout << "copy costructor gerceklesti..";
}
void bankAccount::displayProfile()
{
	cout << "personName:" << personName << "personSurname:" << personSurname << "phone:" << personPhone << "balance:" << accountBalance << endl;


}


int main()
{

	bankAccount account1("Ebru", "Güneş" );
	cout << account1.getPersonName() << endl;
	cout << account1.getPersonSurname() << endl;
	cout << account1.getPersonPhone() << endl;
	cout << account1.getPersonBalance() << endl;


	bankAccount account2(account1);

	bankAccount account3(" Kerem", "Yıldız");
	cout << account3.getPersonName() << endl;
	cout << account3.getPersonSurname() << endl;
	cout << account3.getPersonPhone() << endl;
	cout << account3.getPersonBalance() << endl;
	


return0;



}
