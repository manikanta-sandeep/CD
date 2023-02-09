# CD


```
%{
int i=0;
int c=0;
%}
%%
([a-zA-Z0-9])* {i++;}
"\n" {c++;}
"," {printf("No of words are: %d and No of Lines are: %d \n",i,c);return 0;}
%%

int yywrap(void){}
int main()
{
        yylex();
        return 0;
}


```
