# CD


### keywords

```
#include<stdio.h>
#include<string.h>
int main(){
char
*a[11]={"for","int","main","char","float","include","while","String","long","double","return"};
char b[100];
scanf("%[^\n]%*c",b);
int flag=1;
for(int i=0;i<11;i++){
if (strcmp(a[i],b)==0){
printf("It is a keyword\n");
flag=0;
}
}
printf("%d\n",flag);
if (flag){
printf("It is not a keyword\n");
}
}

```
### identifiers.c

```
#include<stdio.h>
#include<string.h>
int main(){
char b[100];
scanf("%s",b);
int flag=1;
if (((b[0]>='a' && b[0]<='z') || (b[0]>='A' && b[0]<='Z')) || (b[0]=='_')){
int i=1;
flag=2;
while (b[i]!='\0'){
if (!(((b[i]>='a' && b[i]<='z') || (b[i]>='A' && b[i]<='Z')) || (b[i]=='_') || (b[i]>='0'
&& b[i]<='9'))){
flag=0;
break;
}
i+=1;
}
}
}
if(flag==2){
printf("Valid identifier\n");
}
else{
printf("It is not a valid Identifier\n");
}

```

### Input from source file

```
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
int iskeyword(char b[20]){
char *a[32]={
"auto","double","int","struct","break","else","long",
"switch","case","enum","register","typedef","char",
"extern","return","union","const","float","short",
"unsigned","continue","for","signed","void","default",
"goto","sizeof","voltile","do","if","static","while"
};
int flag=1;
for(int i=0;i<32;i++){
if (strcmp(a[i],b)==0){
flag=0;
return 1;
}
}
if (flag){
return 0;
}
}
int isidentifier(char b[20]){
int flag=1;
if (((b[0]>='a' && b[0]<='z') || (b[0]>='A' && b[0]<='Z')) || (b[0]=='_')){
int i=1;
flag=2;
while (b[i]!='\0'){
if (!(((b[i]>='a' && b[i]<='z') || (b[i]>='A' && b[i]<='Z')) || (b[i]=='_') || (b[i]>='0'
&& b[i]<='9'))){
flag=0;
break;
}
}
}
i+=1;}
if(flag==2){
return 1;
}
else{
return 0;
}
int isoperator(char k){
char op[]="+-*/%=";
for(int i=0;i<6;i++){
if(op[i]==k){
return 1;
}
}
return 0;
}
int main() {
FILE *file;
char c;
file=fopen("keywords.c","r");
char *identifiers[1000];
char *keywords[1000];
char b[100];
if(file==NULL){
printf("Cant open the file");
}
else{
int i=0;int id_count=0;int k_count=0;
while((c=fgetc(file))!=EOF){
printf("%c",c);
if(c=='\n'||c==' '||isoperator(c)==1||c==';'){
b[i]='\0';
if(iskeyword(b)==1){
keywords[k_count]=malloc(10*sizeof(char));
strcpy(keywords[k_count],b);
k_count+=1;
}
else if(isidentifier(b)==1){
identifiers[id_count]=malloc(10*sizeof(char));
strcpy(identifiers[id_count],b);
id_count+=1;
}
memset(b,'\0',sizeof(b));
i=0;
}
else{
if(c=='\t'){}
continue;
b[i]=c;
i+=1;
}
}
}
fclose(file);
printf("\nFile successfully read\n");
printf("\nIdentifiers are:\n");
for(int i=0;i<id_count;i++){
printf("%d %s\n",i,identifiers[i]);
printf("\nKeywords are:\n");
for(int i=0;i<k_count;i++){
printf("%d %s\n",i,keywords[i]);
}
}
}
```

### sourcefile
```
#include<stdio.h>
#include<string.h>
int main(){
char
*a[11]={"for","int","main","char","float","include","while","String","long","double","return"};
char b[100];
scanf("%[^\n]%*c",b);
int flag=1;
for(int i=0;i<11;i++){
if (strcmp(a[i],b)==0){
printf("It is a keyword\n");
flag=0;
}
}
}
printf("%d\n",flag);
if (flag){
printf("It is not a keyword\n");
}
```
### 
### Counting Number of lines and words
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
