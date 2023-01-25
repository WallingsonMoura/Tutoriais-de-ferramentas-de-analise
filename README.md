
### Anaconda
Anaconda é um gerenciador de pacotes e ambiente de integração de diversos softwares.
- Copiar o link de download do instalador Anaconda para linux no em:
https://www.anaconda.com/products/distribution#Downloads.

- Utilizar o comando ```$ wget [link de download]```.
- Utilizar o comando ```$ sudo chmod +x Anaconda3-2022.10-Linux-x86_64.sh``` (essa foi a versão que fiz o download), para permitir a execução do instalador.
- Utilizar o comando ```$ ./Anaconda3-2022.10-Linux-x86_64.sh``` para iniciar a instalação, em seguida escolha o local de instalação.

### Instalando Fastx ToolKit
kit de ferramentas de pré-processamento de leituras curtas FastQ/A.
- Utilizar o comando ```$ conda install -c bioconda fastx_toolkit```.
##### Convertendo .FastQ para .Fasta:
- Utilizar o comando ```$ fastq_to_fasta -i [arquivo.fastq] -o [arquvio.fasta]```.
- Site com alguns comandos:
hannonlab.cshl.edu/fastx_toolkit/commandline.html#command_line_arguments

### FastQC
Ferramenta de controle de qualidade para dados de sequênciamento de alto rendimento.
##### Anaconda
- Utilizar o comando ```$ conda install -c bioconda fastqc```.
- Em breve instruções para utilizar o programa por linha de comando...
##### Windows
- Fazer o download no endereço: https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.9.zip
- Descompactar o arquivo, e copiar o executável```.bat``` para área de trabalho.
- OBS: A máquina que vai rodar o programa deve ter uma versão compatível do java instalada.
- Manual do *FastQC*: https://dnacore.missouri.edu/PDF/FastQC_Manual.pdf
##### Ubuntu
- Utilizar o comando ```$ wget https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.9.zip```, para fazer o download do programa.
- Utilizar o comando ```$ tar xfv fastqc_v0.11.9.zip``` para descompactar o arquivo.
- Acessar o diretório ```~/FastQC``` através do terminal, e utilizar o comando ```$ sudo chmod 755 fastqc``` para conceder as permissões necessárias ao programa.
- Mover os arquivos que deseja analisar para o diretório ```~/FastQC```, e no terminal utilizar o comando ```$ ./fastqc [arquivos que deseja analisar]```, para analisar a qualidade dos arquivos, obtendo assim um arquivo de saida em ```.html``` com o resultado das análises.

### Trimmomatic
Ferramenta de corte utilizada para aparar dados Ilumina NGS.
##### Anaconda:
- Utilizar o comando ```$ conda install -c bioconda trimmomatic```.
- Em breve instruções para utilizar o programa...
##### Ubuntu:
- Fazer o download com o comando ```$ wget http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip```
- Extrair o arquivo com o comando ```$ tar xfv [arquivo]```.
- Acessar a pasta ```/Trimmomatic-0.39/adapters``` copiar os adaptadores e colar na pasta ```/Trimmomatic-0.39```.
- Mover arquivos que serão trimados para a pasta ```/Trimmomatic-0.39```
- Acessar o diretório ```~/Trimmomatic-0.39```.
- Para arquivos *paired end*, utilizar o comando ```$ java -jar trimmomatic-0.39.jar PE [input_Forward.fastq.gz] [input_Reverse.fastq.gz] [output_Forward_paired.fq.gz] [output_Forward_unpaired.fq.gz] [output_Reverse_paired.fq.gz] [output_Reverse_unpaired.fq.gz] ILLUMINACLIP:Adaptador-PE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:36```.
- Para arquivos *single end*, utilizar o comando ```$ java -jar trimmomatic-0.39.jar SE [input.fastq.gz] [output.fastq.gz] ILLUMINACLIP:Adaptador-SE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:36```.
- Em ambos os comandos o usuário pode escolher os parâmetros que atendam melhor suas exigências.
- Manual do *Trimmomatic*: http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/TrimmomaticManual_V0.32.pdf
- Algumas sequências *Paired end* são depositadas no NCBI contendo as sequências nos sentidos forward e reverse juntas em um único arquivo. Para realizar a trimagem deve-se separar essas sequências em dois arquivos distintos, para isso utilizar a ferramenta SRA-tollkit.

### SRA-toolkit
Kit de ferramentas do NCBI para baixar e/ou separar arquivos SRA.
##### Anaconda
- Utilizar o comando ```$ conda install -c bioconda sra-tools```.
- Em breve instruções para utilizar o programa...
##### Ubuntu
- Fazer o download do arquivo com o comando ```$ wget https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.1/sratoolkit.3.0.1-ubuntu64.tar.gz```.
- Utilizar o comando ```$ tar vxzf [arquivo baixado]```, para descompactar o arquivo.
- Utilizar o comando ```$ export PATH=$PATH:$PWD/sratoolkit.3.0.1-ubuntu64/bin```.
- Mover o arquivo que deseja separar para o diretorio principal do usuário. (O arquivo deve estar no formato .SRA orginal).
- Para separar o arquivo em forward e reverse, utilizar o comando ```$ ./fastq-dump --split-files [arquivo]```.
- Tambem é possível fazer o download do arquivo em .SRA e ao mesmo tempo separa-lo em dois arquivos, forward e reverse, utilizando o comando ```$ fasterq-dump --split-files [código do sra]```.
- Para obter instruções de uso consultar o endereço: https://hpc.nih.gov/apps/sratoolkit.html

### BBtools
##### Ubuntu
- Utilizar o comando ```$ wget https://sourceforge.net/projects/bbmap/files/latest/download```, para fazer o download do executável.
- Descompactar o arquivo com o comando ```$ tar xvzf [arquivo]```.
- Para testar a instalação utilize o comando ```$ ~/bbmap/stats.sh in=~/bbmap/resources/phix174_ill.ref.fa.gz```.
- Para mais informações sobre as funcionalidades deste pacote: https://jgi.doe.gov/data-and-tools/software-tools/bbtools/bb-tools-user-guide/.
- Para remover duplicatas da sequência utilizar o comando ```$ ./clumpify.sh in=[arquivo de entrada] out=[arquivo de saída] dedupe allduplicates```.
- No lugar do ```allduplicates``` você pode utilizar ```subs=2``` para deixar as duas melhores cópias das duplicatas no arquivo.
- Para obter instruções de uso consultar o endereço: https://jgi.doe.gov/data-and-tools/software-tools/bbtools/bb-tools-user-guide/

### Montagem de genomas
Existem varias ferramentas disponíveis para realizar a montagem dos genomas, a escolha da ferramenta que será utilizada fica a critério do bioinformata, que deverá levar em consideração o tipo de amostra que está utilizando e quais são os seus objetivos de análise. A seguir veremos algumas ferramentas que podem ser utilizadas.
### SPAdes
Montador de genomas de São Petersburgo (SPAdes).
##### Anaconda
- Utilizar o comando ```$ conda install -c bioconda spades```.
##### Ubuntu
- Fazer o download do binário com o comando ```$ wget https://cab.spbu.ru/files/release3.15.5/SPAdes-3.15.5-Linux.tar.gz```.
- Descompactar o arquivo e conceder permissões utilizando o comando ```$ tar -xzf [arquivo baixado]```.
- Acessar o diretório onde o arquivo esta e utilizar os comandos.
- Caso seu Ubuntu seja WSL, este binário pode apresentar incompatibilidade. Uma solução para este problema é compilar o código fonte do SPAdes para seu Ubuntu, a seguir segue instruções.
##### Compilando código fonte
- Você precisará das seguintes bibliotecas instaladas no Ubuntu: ```g++ (v. 5.3.1 ou superior)```, ```cmake (v. 3.5 ou superior)```, ```zlib (caso não funcione instalar zlib1g ou zlib1g-dev)```, ```libbz2 (caso não funcione instalar libbz2-dev)```. 
- Caso precise instalar, utilizar o comando ```$ sudo apt-get install [nome da biblioteca]```.
- Fazer o download do código fonte utilizando o comando ```$ wget http://cab.spbu.ru/files/release3.15.5/SPAdes-3.15.5.tar.gz```.
- Descompactar o arquivo e conceder permissões utilizando o comando ```$ tar -xzf [nome do arquivo]```.
- Acessar o diretório onde o arquivo está e utilizar o comando ```$ ./spades_compile.sh```.
##### Utilizando o SPAdes
- Single end, utilizar o comando ```$ ./spades.py -k 21,33,55,77 --careful -s [arquivo de entrada.fq.gz] -o [pasta para arquivos de saída]```.
- Paired end (forward e reverse separados), utilizar o comando ```$ ./spades.py -k 21,33,55,77 --careful -1 [arquivo forward.fq.gz] -2 [arquivo reverse.fq.gz] -o [pasta para arquivos de saída]```.
- Em algumas situações é necessário adicionar ```--only-assembler``` para resolver um erro ```hammer```.
- Manual do SPAdes: https://cab.spbu.ru/files/release3.15.2/manual.html

### Megahit
Em breve...
- Utilizar o comando ```$ conda install -c bioconda megahit```.

### Quast
Ferramenta de avaliação de montagem do genoma. Funciona com e sem genomas de referência. A ferramenta aceita vários conjuntos, portanto é adequada para comparação.
##### Ubuntu
- Fazer o download utilizando o comando ```$ wget https://github.com/ablab/quast/releases/download/quast_5.2.0/quast-5.2.0.tar.gz```.
- Descompactar o arquivo e conceder as permissões necessárias utilizando o comando ```$ tar -xzf quast-5.2.0.tar.gz```.
- Acessar o diretório do arquivo e utilizar o comando ```$ ./setup.py install_full```, para compilar os arquivos da ferramenta.
- Manual do Quast: https://quast.sourceforge.net/docs/manual.html

### Diamond
##### Instalação
- Para fazer o download do binario utilizar o comando ```$ wget http://github.com/bbuchfink/diamond/releases/download/v2.0.14/diamond-linux64.tar.gz```.
- Utilize o comando ```$ tar xzf [arquivo]```, para extrair e conceder as permissões necessárias ao arquivo.
##### Criando banco de dados
- Fazer o download do arquivo RefSeq de proteínas para virus. Disponível no NCBI.
- Utilizar o comando ```$ ./diamond makedb --in [arquivo RefSeq_Protein] --db [arquivo de saída] --taxonmap [arquivo taxonmap] --taxonnames [arquivo taxonnames] --taxonnodes [arquivo taxonnodes]```.
- Link para fazer o download do taxonmap: ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/accession2taxid/prot.accession2taxid.gz.
- Link para fazer o download do taxonnames e taxonnodes: ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/taxdmp.zip.
##### Blastx
- Utilizar o comando ```$ ./diamond blastx -d [banco de dados] -q [contigs qu serão processados] -o [nome do arquivo de saída] -outfmt [código para o formato desejado]```.
- Para alterar o modos de sensibilidade utilizar ```--[modo desejado]```.
- Outros comandos: https://github.com/bbuchfink/diamond/wiki/3.-Command-line-options
- Para vizualizar os resultados utilizar o comando ```$ ./diamond view -a $SAMPLE.search_result.daa > $SAMPLE.search_result.tab```.
- Manual do Diamond: https://usermanual.wiki/Pdf/diamondmanual.1718530976/view

### Blast
Conjunto de ferramentas desenvolvido para realizar buscas e comparar sequências biológicas contra um banco de dados, retornando sequências mais similares, referentes à sequência pesquisada.
- Utilizar o comando ```$ conda install -c bioconda blast```.
Porém com este comando está disponível apenas a versão 2.5.0 (versão desatualizada).
- Copiar o link de download do instalador Blast+ em: https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/
- Utilizar o comando ```$ wget [link de download]```, para fazer o download do instalador.
- Utilizar o comando ```$ tar xzf [nome do arquivo baixado]```, para descompactar o arquivo. 
##### Criando banco de dados
- Acessar site do NCBI e pesquisar por nucleotídeos/proteínas de vírus, arquivo RefSeq.
- Clicar na bandeja “```enviar para```”, depois ```Arquivo >> Formato (Fasta) >>Criar arquivo```.
- Mover o arquivo baixado para o diretorio do Blast.
- Utilizar o comando ```$ makeblastdb -in [nome do arquivo.fasta] -title reference -dbtype nucl -out databases/reference```.
##### tBlastx
- Para fazer um tBlastx, Utilizar o comando ```$ tblastx -db databases/reference -query [sequencia.fasta] -evalue 0.0000000001 -outfmt 5 -max_target_seqs 1 -out [resultado.table] -num_threads [número de núcleos do seu processador]```.
- Manual do BLAST: https://www.ncbi.nlm.nih.gov/books/NBK279691/

### KronaTools
##### Instalação
- Fazer o download do arquivo utilizando o comando ```$ wget https://github.com/marbl/Krona/releases/download/v2.8.1/KronaTools-2.8.1.tar```.
- Para extrair o arquivo e conceder as permissões necessárias utilizar o comando ```$ tar xfv [arquivo]```.

### Sites de bancos de dados:
- NCBI: https://www.ncbi.nlm.nih.gov/
- EBI: https://www.ebi.ac.uk/
