#include<iostream>
using namespace std;

string arr[20], arr2[20], arr3[20], arr4[20], arr5[20];
int total = 0;

void enter()
{
    int choice;

    cout << "How many students do you want to enter: ";
    cin >> choice;

    if(total == 0)
    {
        total = total + choice;

        for(int i=0; i<choice; i++)
        {
            cout << "\nEnter data of student " << i+1 << endl;

            cout << "Enter Name: ";
            cin >> arr[i];

            cout << "Enter Roll No: ";
            cin >> arr2[i];

            cout << "Enter Course: ";
            cin >> arr3[i];

            cout << "Enter Class: ";
            cin >> arr4[i];

            cout << "Enter Contact: ";
            cin >> arr5[i];
        }
    }
    else
    {
        for(int i=total; i<total+choice; i++)
        {
            cout << "\nEnter data of student " << i+1 << endl;

            cout << "Enter Name: ";
            cin >> arr[i];

            cout << "Enter Roll No: ";
            cin >> arr2[i];

            cout << "Enter Course: ";
            cin >> arr3[i];

            cout << "Enter Class: ";
            cin >> arr4[i];

            cout << "Enter Contact: ";
            cin >> arr5[i];
        }

        total = total + choice;
    }
}

void show()
{
    if(total == 0)
    {
        cout << "No data entered" << endl;
    }
    else
    {
        for(int i=0; i<total; i++)
        {
            cout << "\nData of Student " << i+1 << endl;

            cout << "Name: " << arr[i] << endl;
            cout << "Roll No: " << arr2[i] << endl;
            cout << "Course: " << arr3[i] << endl;
            cout << "Class: " << arr4[i] << endl;
            cout << "Contact: " << arr5[i] << endl;
        }
    }
}

void search()
{
    string rollno;

    cout << "Enter roll no of student you want to search: ";
    cin >> rollno;

    bool found = false;

    for(int i=0; i<total; i++)
    {
        if(rollno == arr2[i])
        {
            cout << "\nRecord Found" << endl;

            cout << "Name: " << arr[i] << endl;
            cout << "Roll No: " << arr2[i] << endl;
            cout << "Course: " << arr3[i] << endl;
            cout << "Class: " << arr4[i] << endl;
            cout << "Contact: " << arr5[i] << endl;

            found = true;
        }
    }

    if(found == false)
    {
        cout << "Record not found" << endl;
    }
}

void update()
{
    string rollno;

    cout << "Enter roll no of student you want to update: ";
    cin >> rollno;

    bool found = false;

    for(int i=0; i<total; i++)
    {
        if(rollno == arr2[i])
        {
            cout << "\nPrevious Data" << endl;

            cout << "Name: " << arr[i] << endl;
            cout << "Roll No: " << arr2[i] << endl;
            cout << "Course: " << arr3[i] << endl;
            cout << "Class: " << arr4[i] << endl;
            cout << "Contact: " << arr5[i] << endl;

            cout << "\nEnter New Data" << endl;

            cout << "Enter Name: ";
            cin >> arr[i];

            cout << "Enter Roll No: ";
            cin >> arr2[i];

            cout << "Enter Course: ";
            cin >> arr3[i];

            cout << "Enter Class: ";
            cin >> arr4[i];

            cout << "Enter Contact: ";
            cin >> arr5[i];

            cout << "Record updated successfully" << endl;

            found = true;
        }
    }

    if(found == false)
    {
        cout << "Record not found" << endl;
    }
}

void deleterecord()
{
    int a;

    cout << "Press 1 to delete all records" << endl;
    cout << "Press 2 to delete specific record" << endl;
    cin >> a;

    if(a == 1)
    {
        total = 0;
        cout << "All records deleted" << endl;
    }

    else if(a == 2)
    {
        string rollno;

        cout << "Enter roll no you want to delete: ";
        cin >> rollno;

        bool found = false;

        for(int i=0; i<total; i++)
        {
            if(rollno == arr2[i])
            {
                for(int j=i; j<total-1; j++)
                {
                    arr[j] = arr[j+1];
                    arr2[j] = arr2[j+1];
                    arr3[j] = arr3[j+1];
                    arr4[j] = arr4[j+1];
                    arr5[j] = arr5[j+1];
                }

                total--;

                cout << "Record deleted successfully" << endl;

                found = true;
                break;
            }
        }

        if(found == false)
        {
            cout << "Record not found" << endl;
        }
    }
}

int main()
{
    int value;

    while(true)
    {
        cout << "\n******** STUDENT MANAGEMENT SYSTEM ********\n";

        cout << "Press 1 to enter data" << endl;
        cout << "Press 2 to show data" << endl;
        cout << "Press 3 to search data" << endl;
        cout << "Press 4 to update data" << endl;
        cout << "Press 5 to delete data" << endl;
        cout << "Press 6 to exit" << endl;

        cout << "Enter your choice: ";
        cin >> value;

        switch(value)
        {
            case 1:
                enter();
                break;

            case 2:
                show();
                break;

            case 3:
                search();
                break;

            case 4:
                update();
                break;

            case 5:
                deleterecord();
                break;

            case 6:
                exit(0);

            default:
                cout << "Invalid choice" << endl;
        }
    }
}
