Código fonte:


/* Começo Matriz*/ 
char *name; 
char *email; 
char *cpf; 
char *birthDay; 
char *phoneNumber; 
char *street; 
char *streetNumber; 
char *neighborhood; 
char *city; 
char *state; 
char *cep; 
char *diagnosisDay; 
char *comorbidity; 

// variavel para leitura de dados 
char leitura[50]; 
// variavel de tratamento do registro 
char registro[297]; 
// ponteiro para arquivo 
FILE *fp; 
// FUNÇÕES 
int validate_password() { 
char login[20]; 
char senha[20]; 
int i, senha_ok; 
char c; 

do { 
system("CLS"); 
printf(">>> Sistema de cadastro de pacientes diagnosticados com Covid-19 >>>\n\n\n\n\n"); 
fflush(stdin); 
printf("Login: "); 
gets(login); 
printf("\nSenha: "); 
i = 0; 
while((c=getch())!=13){ //13 é o valor de ENTER na tabela ASCII 
senha[i]=c; 
i++; 
printf("*"); //imprime o * Anterisco 
} 

senha[i]='\0'; 
senha_ok = strcmp(senha, "luciano"); 
if(!senha_ok) return 1; 
} while (senha_ok); 
} 
int read_option(){ // Ler opções do programa 
int opcao, passagem = 0; 
do { 
system("cls"); 
printf("Menu Principal\n"); 
printf("--------------\n"); 
printf("1- Cadastrar Paciente\n"); 
printf("2- Consultar Paciente\n"); 
printf("3- Pesquisar Paciente (Nome/CPF)\n"); 
printf("0- Sair do Programa\n"); 
if (passagem) 
printf("\n *** Opção inválida!\n"); 
printf ("Escolha uma das opções:\n"); 
printf(">>> "); 
scanf("%d",&opcao); 
getchar(); 
printf("\n"); 
if (opcao != 0 && opcao != 1 && opcao != 2 && opcao != 3) passagem = 1; 
} while (opcao != 0 && opcao != 1 && opcao != 2 && opcao != 3); 
return opcao; 
} 

/* 
void pause(char mensagem[]){ 
printf("%s",mensagem); 
getch(); 
} 
*/ 
void preencher_espacos(char *sequencia, int tamanho) { 
int tam, espacos, i; 
strcat(registro, sequencia); 
tam = strlen(sequencia); 
espacos = tamanho - tam; 
for (i=1;i<=espacos;i++) strcat(registro, " "); 
} 
void tratar_registro() { 
preencher_espacos(name, 50); 
preencher_espacos(email, 50); 
strcat(registro, cpf); 
strcat(registro, birthDay); 
preencher_espacos(phoneNumber, 15);

{ 
printf ("** Erro: Memoria Insuficiente **"); 
free(comorbidity); 
return 0; 
} 
strcpy(comorbidity, leitura); 
tratar_registro(); 
if (salvar()) printf ("\n\nDados do paciente salvo em arquivo!\n\n"); 
else printf ("\n\nHouve um problema com a manipulação do arquivo.\n\n"); 

free(name); 
free(email); 
free(cpf); 
free(birthDay); 
free(phoneNumber); 
free(street); 
free(streetNumber); 
free(neighborhood); 
free(city); 
free(state); 
free(cep); 
free(diagnosisDay); 
free(comorbidity); 
printf ("\n\nTamanho do registro: %d caracteres\n\n", strlen(registro)); 
system("pause"); 
return 1; 
} 

/* 
int comorbidity_option() { // ler tipos de comorbidades 
printf("Qual o tipo de comorbidade?\nEscolha entre as opções:\n"); 
printf("1- Diabetes"); 
printf("2- Obesidade\n"); 
printf("3- Hipertensão\n"); 
printf("4- Tuberculose\n"); 
printf("Opção: "); 
scanf("%d",&x); 
printf("\n"); 
return x;

} 
*/ 
int consultar() { 
system("cls"); 
FILE *fp; 
fp = fopen("arquivo.txt", "r"); 
if (fp == NULL) {

return 0; 
} 
fscanf(fp, "%s", &name); 
fscanf(fp, "%s", &email); 
fscanf(fp, "%s", &cpf); 
fscanf(fp, "%s", &birthDay); 
fscanf(fp, "%s", &phoneNumber); 
fscanf(fp, "%s", &street); 
fscanf(fp, "%s", &streetNumber); 
fscanf(fp, "%s", &neighborhood); 
fscanf(fp, "%s", &city); 
fscanf(fp, "%s", &state); 
fscanf(fp, "%s", &cep); 
fscanf(fp, "%s", &diagnosisDay); 
fscanf(fp, "%s", &comorbidity); 
fclose(fp); 
return 1; 

} 
void pesquisar() { 
system("cls"); 
printf("\nInforme o CPF da pessoa: "); 
long long cpf_localizador; 
scanf("%Lu",&cpf_localizador); 
printf ("*** Consulta de Paciente ***\n\n\n\n\n"); 
printf ("Nome do Paciente: %s\n", name); 
printf ("E-mail: %s\n", email); 
printf ("Data de Nascimento: %s\n", birthDay); 
printf ("Telefone: %s\n", phoneNumber); 
printf ("Data do diagnostico: %s\n", diagnosisDay); 
printf ("Comorbidade: %s\n", comorbidity); 
printf ("\n\n * Dados do paciente recuperados do arquivo *\n\n"); 
system("pause"); 
}

void imprimir() { 
system("cls"); 
printf ("*** Consulta de Paciente ***\n\n\n\n\n"); 
printf ("Nome do Paciente: %s\n", name); 
printf ("E-mail: %s\n", email); 
printf ("Data de Nascimento: %s\n", birthDay); 
printf ("Telefone: %s\n", phoneNumber); 
printf ("Endereço:\n"); 
printf ("%s número: %s bairro: %s\n", street, streetNumber, neighborhood); 
printf ("cidade: %s estado: %s CEP: %s\n", city, state, cep); 
printf ("Data do diagnóstico: %s\n", diagnosisDay); 
printf ("Comorbidade: %s\n", comorbidity); 
printf ("\n\n * Dados do paciente recuperados do arquivo *\n\n"); 
} 
// FIM FUNÇÕES
