### Instalando Ubuntu no Windows
- Fazer o download do Ubuntu 22.04.1 LTS (WSL) e instalar.
- Após instalado utilizar os comandos ```$ sudo apt-get update```, e ```$ sudo apt-get upgrade```, para atualizar o sistema.

### Instalando Anaconda
- Copiar o link de download do instalador Anaconda para linux no em:
https://www.anaconda.com/products/distribution#Downloads.

Utilizar o comando $ wget [link de download].
Utilizar o comando $ sudo chmod +x Anaconda3-2022.10-Linux-x86_64.sh (essa foi a versão que fiz o download), para permitir a execução do instalador.
Utilizar o comando $ ./Anaconda3-2022.10-Linux-x86_64.sh para iniciar a instalação, em seguida escolha o local de instalação.

Instalando FastQC: Ferramenta de controle de qualidade para dados de sequência de alto rendimento.
Utilizar o comando $ conda install -c bioconda fastqc.

Instalando Trimmomatic: Ferramenta de corte de leitura flexível para dados Ilumina NGS.
Utilizar o comando $ conda install -c bioconda trimmomatic.
Instalando e utilizando Trimmomatic em WSL:
Fazer o download em: http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip
Extrair o arquivo e mover a pasta para: \\wsl.localhost\Ubuntu-22.04\home\wallingson_moura
Acessar a pasta /Trimmomatic-0.39/adapters copiar os adaptadores e colar na pasta /Trimmomatic-0.39
Mover arquivos que serão trimados para a pasta /Trimmomatic-0.39
Acessar o diretório /Trimmomatic-0.39 e utilizar o comando:
$ java -jar trimmomatic-0.39.jar PE SRR17886362__Forward.fastqsanger.gz SRR17886362__Reverse.fastqsanger.gz SRR17886362__Forward_paired.fq.gz SRR17886362__Forward_unpaired.fq.gz SRR17886362__Reverse_paired.fq.gz SRR17886362__Reverse_unpaired.fq.gz ILLUMINACLIP:NexteraPE-PE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:36


Instalando SPAdes: (montador de genomas de São Petersburgo) destina-se tanto para isolados padrão quanto para conjuntos de bactérias MDA de células únicas.
Utilizar o comando $ conda install -c bioconda spades.

Instalando Megahit: uma solução de nó único ultra rapido para montagem de metagenômica grande e complexa através de gráfico sucinto Bruijn.
Utilizar o comando $ conda install -c bioconda megahit.

Instalando Blast+: conjunto de ferramentas blast que utiliza o NCBI C++ ToolKit
Utilizar o comando $ conda install -c bioconda blast.
Porém com este comando está disponível apenas a versão 2.5.0 (versão desatualizada).
Copiar o link de download do instalador Blast+ em: https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/
Utilizar o comando $ wget [link de download], para fazer o download do instalador.
Utilizar o comando $ tar xzf [nome do arquivo baixado], para descompactar o arquivo. 

Instalando Mafft: Programa de alinhamento múltiplo para sequências de aminoácidos ou nucleotídeos baseados na rápida transformação de Fourier.sudo apt-
Utilizar o comando $ conda install -c bioconda mafft.

Instalando Jmodeltest
Instalando Protest
Instalando MrBayes
Instalando Beast
Instalando Figtree
Instalando Itol
Instalando SDT

Instalando Fastx ToolKit: kit de ferramentas de pré-processamento de leituras curtas FastQ/A.
Utilizar o comando $ conda install -c bioconda fastx_toolkit.
Convertendo .FastQ para .Fasta: utilizar o comando $ fastq_to_fasta -i [arquivo.fastq] -o [arquvio.fasta].
Site com alguns comandos:
hannonlab.cshl.edu/fastx_toolkit/commandline.html#command_line_arguments

Criando banco de dados
Acessar site do NCBI e pesquisar por nucleotídeos de vírus. https://www.ncbi.nlm.nih.gov/nuccore.
Clicar na bandeja “enviar para”, depois Arquivo >> Formato (Fasta) >>Criar arquivo.
Utilizar o comando $ makeblastdb -in [nome do arquivo.fasta] -title reference -dbtype nucl -out databases/reference.

Explosão
Utilizar o comando $ tblastx -db databases/reference -query [sequencia.fasta] -evalue 0.0000000001 -outfmt 5 -max_target_seqs 1 -out [resultado.table] -num_threads [número de núcleos do seu processador].

Sites de bancos de dados:
NCBI:
EBI: https://www.ebi.ac.uk/



Dicionário
Pipeline: uma série de etapas que devem ser executadas para realizar o processamento dos dados.
NGS: sequenciamento de nova geração, também chamado de sequenciamento de alto rendimento, é um conjunto de técnicas de sequenciamento genético que apresentam melhorias em relação ao processo original de sequenciamento de Sanger (ex: sequenciamento Ilumina). Esses métodos de sequenciamento de DNA e RNA empregam processos paralelos em grande escala para execuções mais rápidas e com melhor custo-benefício.Possibilita o sequenciamento de amostras menores e o tempo e esforço para preparo das amostras também são menores.
Reads: fragmentos curtos de DNA.
Contings: fragmentos de DNA sobrepostos. Alinhamento multiplo de leituras (reads) de onde é extraída uma sequencia consenso.
Transcriptoma: conjunto de RNA’s transcritos por um organismo
De novo: sequenciamento de genoma novo na ausência de uma sequência de referência.
Mers: pequenos fragmentos de reads.
K-mers: mers no tamanho k.
Scaffolds: supercontings

Extração -> Preparação da biblioteca (amplificação para produzir um pool de sequências de destino de tamanho apropriado, e, adição de adaptadores de sequenciamento que mais tarde interagirão com a plataforma NGS
