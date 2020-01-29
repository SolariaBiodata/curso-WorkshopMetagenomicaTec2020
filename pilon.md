---
permalink: /pilon.html
---
![alt text](https://solariabiodata.com.mx/images/solaria_banner.png "Soluciones de Siguiente Generación")
# Nextera DNA Workshop - Sesión Bonus de Asignación Taxonómica

## Sesión Práctica

### Descripción
En esta sesión de Bonus estaremos realizando el análisis bioinformático de taxonomía, que utiliza datos de Whole DNA Shotgun Sequencing, y que necesita realizar un ensamble de genoma completo.

### Requisitos

Para poder realizar este ejercicio, necesitaremos:

1. Datos de secuencias:
    - Puedes usar tus propias secuencias, en formato FASTQ o FASTQ.GZ
2. Acceso a los siguientes recursos de internet:
    - Página de [NCBI](https://www.ncbi.nlm.nih.gov/)
    - Página de [SRA](https://www.ncbi.nlm.nih.gov/sra)
3. Sofware Recomendable para esta sesión:
    - Terminal (Mac o Linux)
    - Putty (Windows)
    - WinSCP (Windows)

## Ejercicio 01: Asignación Taxonómica
### Descripción
Utilizaremos como base, un programa que extrae genes marcadores de copia única: Metaphlan2.

### Instrucciones
1. Ejecutamos el siguiente comando en nuestra terminal
        metaphlan2.py  sample_1_R1.fastq, sample_1_R2.fastq \
        --mpa_pkl  ~/metaphlan2/metaphlan_databases/mpa_v20_m200.pkl \
        --bowtie2db ~/metaphlan2/metaphlan_databases/mpa_v20_m200 \
        --bt2_ps very-sensitive
        --bowtie2out out_sample.bz2
        --nproc 2
        --input_type fastq
        -o meta_sample_1.out

## Ejercicio 02: Generación de Krona

### Descripción
Por último, de la tabla generada por el programa anterior, realizaremos un diagrama circular donde podremos ver la abundancia a diferentes niveles taxonómicos, con Krona.
### Instrucciones
1. Transformaremos la tabla generada anteriormente con
        ~/metaphlan2/utils/metaphlan2krona.py -p sample1_metaphlan.txt -k meta_sample_1.out
2. Para generar nuestro diagrama
        ktImportText -o  sample_1_krona.html   meta_sample_1.out
3. Por último, podemos ver nuestro archivo desde el navegador preferido
