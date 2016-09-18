//# Sudoku
//Program to simulate a sudoku puzzle


#include <iostream>
#include <vector>


using namespace std;
using std::vector;

//Initialize vector array to contain puzzle
void print(vector <vector<int> > nums)
{
 for (int i=0; i<3; i++)
        {
            for (int j=0; j<3; j++)
                {cout << nums[i][j] << " ";}
                cout << " ";
               for (int j=3; j<6; j++)
                {cout << nums[i][j] << " ";}
                cout << " ";
                for (int j=6; j<9; j++)
                {cout << nums[i][j] << " ";}
                cout << "\n";}
                cout << endl;
        for (int i=3; i<6; i++)
        {
            for (int j=0; j<3; j++)
                {cout << nums[i][j] << " ";}
                cout << " ";
               for (int j=3; j<6; j++)
                {cout << nums[i][j] << " ";}
                cout << " ";
                for (int j=6; j<9; j++)
                {cout << nums[i][j] << " ";}
                cout << "\n";}
                cout << endl;
        for (int i=6; i<9; i++)
        {
            for (int j=0; j<3; j++)
                {cout << nums[i][j] << " ";}
                cout << " ";
               for (int j=3; j<6; j++)
                {cout << nums[i][j] << " ";}
                cout << " ";
                for (int j=6; j<9; j++)
                {cout << nums[i][j] << " ";}
                cout << "\n";}
}
void input(int rowinput,int columninput,int dit)
{
    cout << "\nInput the row followed by the column of the location you would like to edit:\n";
    cout << "\nRow: "; cin >> rowinput;
    while (rowinput>9 || rowinput<1)
    {
        cout << "\nThat is not a valid row location.\n";
        cout << "\nInput the row of the location you would like to edit:\n";
    cout << "\nRow: "; cin >> rowinput;
    }
    cout << "\nColumn: "; cin >> columninput;
    while (columninput>9 || columninput<1)
    {
        cout << "\nThat is not a valid column location.\n";
        cout << "\nInput the column of the location you would like to edit:\n";
        cout << "\nColumn: "; cin >> columninput;
    }
    cout << "\nInput the value of the number you would like to enter: "; cin >> dit;
    while (dit>9)
    {
        cout << "\nThat is not a valid number value.\n";
        cout << "\nInput the value of the number you would like to enter: ";
        cin >> dit;
    }
}
void rules()
{
    cout << "\nRules:\nIn any game of Sudoku, there will be one big square with 9 smaller squares inside.";
        cout << "\nEach of these smaller squares also have nine smaller squares with numbers inside each of them.\n";
        cout << "In other words, the numbers which appear in the smaller squares will be in groups of 9, with 3 in each row and column.\n";
        cout << "Additionally, each row, column, and square consisting of 9 numbers cannot repeat a number.\n";
        cout << "This means that the numbers 1-9 should all exist one time in each row, column, and square nine separate times once the puzzle has been completed.\n";
}
void array3(vector< vector<int> >nums,int row[3],int column[3],int number,int value)
{
int num=number;
    for (int i=0; i<num; i++)
    {
        for (int j=0;j<num;j++)
        {nums[row[i]][column[j]]=value;}
    }
}
void array4(vector< vector<int> >nums,int row[4],int column[4],int number,int value)
{
int num=number;
    for (int i=0; i<num; i++)
    {
        for (int j=0;j<num;j++)
        {nums[row[i]][column[j]]=value;}
    }
}
void array5(vector< vector<int> >nums,int row[5],int column[5],int number,int value)
{
int num=number;
    for (int i=0; i<num; i++)
    {
        for (int j=0;j<num;j++)
        {nums[row[i]][column[j]]=value;}
    }
}
vector createpuzzle()
{
    int num;
    int row[9];
    int column[9];
    vector < vector<int> > nums(9,vector<int>(9,0));
    for(int i=1;i<10;i++)
    {
    if (i==1)
    {int row[3] = {1,6,8};
    int column[3] = {5,6,2};num=3;
    array3(nums,row,column,num,i);}
    if (i==2)
    {int row[3] = {2,3,6};
    int column[3] = {2,5,3};num=3;
    array3(nums,row,column,num,i);}
    if (i==3)
    {int row[5] = {2,4,6,8,9};
    int column[5] = {9,2,8,7,3};num=5;
    array5(nums,row,column,num,i);}
    if (i==4)
    {int row[4] = {1,2,4,5};
    int column[4] = {7,5,9,2};num=4;
    array4(nums,row,column,num,i);}
    if (i==5)
    {int row[5] = {2,4,5,6,8};
    int column[5] = {8,4,1,9,5};num=5;
    array5(nums,row,column,num,i);}
    if (i==6)
    {int row[5] = {1,2,5,7,8};
    int column[5] = {4,3,8,5,1};num=5;
    array5(nums,row,column,num,i);}
    if (i==7)
    {int row[4] = {3,4,6,9};
    int column[4] = {2,7,1,5};num=4;
    array4(nums,row,column,num,i);}
    if (i==8)
    {int row[3] = {2,8,9};
    int column[3] = {4,8,6};num=3;
    array3(nums,row,column,num,i);}
    else
    {int row[3] = {4,5,7};
    int column[3] = {1,9,6};num=3;
    array3(nums,row,column,num,i);}
    }
    return nums
}

int checkcomplete(vector <vector<int> > nums)
{
int bin,zero;
for (int i;i<9;i++)
{
    for(int j;j<9;j++)
    {
        if (nums[i][j]==0)
            {zero=0; i=9; j=9;}
        else
            zero=1;
    }
}
(zero==1) ? bin=1 : bin =0;
return bin;
}
void detecterror(vector <vector<int> > nums, int rowinput, int columninput, int dit)
{
    int error=1;
        while (error==1)
        { error=0;
        //Find repeat numbers in rows
        int foundrow=0;
        for (int i=0; i<9; i++)
            {
                if(nums[rowinput-1][columninput-1]==nums[rowinput-1][i])
                {
                    foundrow++;
                    //There are repeat numbers in this row
                    if (foundrow != 1)
                    {
                        cout << "foundrow: " << foundrow;
                        error=1;
                        foundrow=0;
                        cout << "\nError! There is a repeated number in this row!\n";
                        i=9;
                    }
                }
            }
        //Find repeat numbers in column
        int foundcolumn=0;
        for (int i=0; i<9; i++)
            {
                if(nums[rowinput-1][columninput-1]==nums[i][columninput-1])
                {
                    foundcolumn++;
                    //There are repeat numbers in this column
                    if (foundcolumn != 1)
                    {
                        error=1;
                        foundcolumn=0;
                        cout << "\nError! There is a repeated number in this column!\n";
                    i=9;
                    }
                }
            }
        //Detect duplicates in square
        int foundsquare=0;
        int k=0;
        int h=0;
        int bound[4] = {0,3,6,9};
        if (rowinput <4)
        {
            k=0;
        }
        if (rowinput>3 && rowinput<7)
        {
            k=1;
        }
        if (rowinput>6)
        {
            k=2;
        }
        if (columninput <4)
        {
            h=0;
        }
        if (columninput>3 && columninput<7)
        {
            h=1;
        }
        if (columninput>6)
        {
            h=2;
        }
        for (int i=bound[k]; i<bound[k+1]; i++)
            {
                for (int j=bound[h]; j<bound[h+1]; j++)
                {
                if(nums[rowinput-1][columninput-1]==nums[i][j])
                    {
                    foundsquare++;
                    //There are repeat numbers in this square
                    if (foundsquare != 1)
                        {
                        error=1;
                        foundsquare=0;
                        cout << "\nError! There is a repeated number in this square!\n";
                    //Ensure that loop will not restart
                    i=bound[k+1];
                    j=bound[h+1];
                        }
                    }
                }
            }
             //Prompt user for input again
             if (error==1)
                {
                    //Reset initial input value
                    nums[rowinput-1][columninput-1]=0;
                        input;
                        //Re-apply user input
                        nums [rowinput-1][columninput-1]=dit;
                }
        }
}

int main()
{

    cout << "Welcome to Sudoku!\n\nIn order to play the game, you will have to fill in all of the zeros which appear.\n";
    cout << "These zeros correspond to what would normally be blank spaces in a regular game of Sudoku.\n";
    cout << "\nDo you know the rules to Sudoku? Type 'Y' for yes or 'N' for no.\n\n";
    char Exp;
    cin >> Exp;
    while (Exp != 'Y' && Exp != 'y' && Exp != 'N' && Exp != 'n')
           {
              cout << "\nDo you know the rules to Sudoku? Type 'Y' for yes or 'N' for no.\n\n";
              cin >> Exp;
           }
    if (Exp == 'N' || Exp == 'n')
    {
        rules;

    }
    cout << "\nThis puzzle will be Beginner difficulty.\n\n";
    //Puzzle Database
    vector < vector<int> > nums(9,vector<int>(9,0));
    //Input data into vector array
    nums=createpuzzle();
    //Output initial puzzle
    print(nums);

    // While loop for solving puzzle
        //Prompt user for input information
        int solve;
    while(solve!=1)
    {
    int rowinput,columninput,dit;
    input;
        //Apply user input to puzzle
    nums[rowinput-1][columninput-1]=dit;
        //Check validity of input
    detecterror(nums,rowinput,columninput,dit);
        //End of error detection loop
        //Output new puzzle
        print(nums);
        //run solve check
        solve=checkcomplete(nums);
    }
    return 0;
}


