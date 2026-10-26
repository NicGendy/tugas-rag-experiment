# RAG Parameter Exploration

## Informasi Eksperimen

**Nama PDF:**

HowtoReadPaper.pdf

**Jumlah halaman PDF:**

3 halaman

**Isi / topik PDF secara singkat:**

Artikel panduan akademik karya S. Keshav dari University of Waterloo yang menjelaskan cara tiga tahap atau *three-pass approach* yang praktis dan efisien untuk membaca *research paper*, serta cara memakai cara tersebut untuk melakukan *literature survey*.

------------------------------------------------------

# Pertanyaan Pengujian

## Pertanyaan 1

What are the steps in the first pass of reading a paper, and what are the five Cs that you should be able to answer at the end of it?

## Pertanyaan 2

What are the three steps to do a literature survey using the three-pass approach?

------------------------------------------------------

# Baseline Configuration

Tuliskan konfigurasi awal sebelum eksperimen.

```text
Temperature:
TOP_K:
Chunk Size:
Chunk Overlap:
Embedding Model:
LLM Model:
```

```text
Temperature: 0.2
TOP_K: 4
Chunk Size: 100
Chunk Overlap: 20
Embedding Model: sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2
LLM Model: openai/gpt-oss-120b
```

------------------------------------------------------

# Experiment 1 - Temperature

Gunakan pertanyaan yang sama pada seluruh percobaan.

## Temperature = 0.0

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1):**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings, ignoring the rest of the text.  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.

**Five “Cs”** – The document states that after the first pass you should be able to answer “the five Cs,” but the list of those five items is not included in the uploaded excerpts. Therefore, the specific five Cs cannot be provided from the available context.

#### Pertanyaan 2

The three‑pass method suggests the following three steps when you are carrying out a literature survey:

1. **Locate a small set of recent papers and do a first pass on each** – Use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to find 3‑5 relevant papers, then skim each one (title, abstract, introduction, section headings, figures, and conclusion) to get a general sense of the work【Source: HowtoReadPaper.pdf | Page 2】.  

2. **Do a second pass on the selected papers** – Read the related‑work sections and look for implicit assumptions, missing citations, and possible methodological issues. This pass lets you see how each paper fits into the broader field and identifies gaps you may need to explore【Source: HowtoReadPaper.pdf | Page 2】.  

3. **Do a third, in‑depth pass on the most relevant papers** – Read the papers thoroughly (methods, experiments, results, and discussion) to evaluate their contributions, verify the assumptions you noted, and extract the detailed information needed for your survey【Source: HowtoReadPaper.pdf | Page 1】.

### Observation

*   **Pertanyaan 1**: Jawaban bersifat deterministik dan lugas sesuai dengan teks halaman 1. Empat langkah *first pass* terjawab dengan akurat. Sedangkan untuk "Five Cs", model memberi tahu secara jelas bahwa daftar rinciannya tidak ada dalam kutipan dokumen atau *"not included in the uploaded excerpts"* karena terpotong ke *chunk* lain.
*   **Pertanyaan 2**: Karena *chunk* halaman 2 yang terbawa hanya berisi paragraf pertama Bab 3 yakni *Doing a Literature Survey* yang menyatu dengan kalimat terakhir Sub-bab 2.3 yakni *"implicit assumptions, missing citations..."*, LLM membuat 3 langkah dengan menyatukan informasi tersebut ke dalam susunan **First pass atau Langkah 1 -> Second pass atau Langkah 2 -> Third pass atau Langkah 3** menggunakan konteks dari halaman 1 dan 2.

------------------------------------------------------

## Temperature = 0.2

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1):**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings (ignore the rest of the text).  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.

**Five “Cs”** – The document states that after the first pass you should be able to answer “the five Cs,” but the list of those Cs is not included in the uploaded pages. Therefore the answer to that part was not found in the provided documents.

#### Pertanyaan 2

The three‑pass method suggests the following three steps when you conduct a literature survey:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to locate three‑to‑five recent papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **Do a first pass on each paper** – read each paper quickly (title, abstract, introduction, section headings, conclusions, and skim figures/tables) to obtain a general sense of its content and contributions.【HowtoReadPaper.pdf | Page 1】

3. **Read the related‑work sections** – after the first pass, examine the papers’ related‑work sections to identify implicit assumptions, missing citations, and potential methodological issues, which helps you map the field and spot gaps.【HowtoReadPaper.pdf | Page 2】

### Observation

*   **Pertanyaan 1**: Isi faktual sama persis dengan saat `temperature = 0.0`, hanya ada sedikit perbedaan tanda baca dan pilihan kata atau *wording* seperti penggunaan tanda kurung pada langkah ke-2 `"(ignore the rest of the text)"` dan kalimat `"uploaded pages"`.
*   **Pertanyaan 2**: Terjadi perubahan cara pengelompokan poin dibanding saat `temperature = 0.0`. Bukannya mengurutkan *first, second, third pass*, LLM malah memecah isi paragraf pertama Bab 3 menjadi 3 tahapan kerja yakni **(1) Find a small set of recent papers**, **(2) Do a first pass on each paper**, dan **(3) Read the related-work sections**. Kalimat akhir dari Sub-bab 2.3 yakni *"identify implicit assumptions, missing citations..."* masih ikut terbawa ke langkah ke-3 karena berada di dalam *chunk* yang sama.

------------------------------------------------------

## Temperature = 0.8

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1)**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings, ignoring the rest of the text.  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.

**Five “Cs”** – The document says that after the first pass you should be able to answer the “five Cs,” but it does not list what those five Cs are.  

*Source: HowtoReadPaper.pdf, page 1.*

#### Pertanyaan 2

The three‑pass method for a literature survey consists of:

1. **Search for papers** – Use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to locate 3–5 recent papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **First‑pass reading** – Perform a quick, single‑pass read of each paper to grasp its overall purpose and main contributions.【HowtoReadPaper.pdf | Page 2】

3. **Read the related‑work sections** – After the first pass, examine the related‑work sections of those papers to identify implicit assumptions, missing citations, and potential methodological issues.【HowtoReadPaper.pdf | Page 2】

### Observation

*   **Pertanyaan 1**: Informasi faktual tetap konsisten dan patuh pada konteks tanpa halusinasi*. Gaya bahasa pada bagian "Five Cs" menjadi lebih pendek seperti *"but it does not list what those five Cs are"* dengan tambahan baris kutipan sumber terpisah berhuruf miring yakni `*Source: HowtoReadPaper.pdf, page 1.*` di bagian bawah.
*   **Pertanyaan 2**: Susunan 3 poin yang dikeluarkan sama dengan `temperature = 0.2` seperti **Search for papers -> First-pass reading -> Read the related-work sections**, tetapi dengan *wording* dan judul poin yang jauh lebih pendek serta padat. Selain itu, semua kutipan sumber secara teratur mengarah ke `Page 2`.

------------------------------------------------------

## Kesimpulan Experiment Temperature

Apa perubahan yang paling terlihat?

1.  **Macam Wording dan Pendeknya Kalimat**: Semakin tinggi nilai `temperature`, kalimat penjelasan dan judul poin jadi lebih pendek dan mengalir dibanding nilai `0.0` yang lebih kaku dan panjang.
2.  **Cara Menata/Mengelompokkan Poin**: Pada Pertanyaan 2, ketika *chunk* yang terbawa hanya berisi sebagian isi Bab 3, perubahan `temperature` dari `0.0` ke `0.2`/`0.8` mengubah cara LLM membagi paragraf yang sama menjadi 3 poin langkah. Namun, di semua nilai `temperature`, LLM tetap hanya memakai data dari *chunk* yang ada dan tidak mengarang informasi di luar konteks.

Menurut kalian nilai mana yang paling cocok untuk aplikasi RAG ini?

`temperature = 0.2`.

Kenapa?

Nilai `0.2` memberikan keseimbangan paling pas antara ketepatan data faktual dan kemampuan menyatukan kalimat. Dibandingkan nilai `0.0` yang cenderung kaku saat membagi poin pada Pertanyaan 2, nilai `0.2` bisa memecah tahapan di dalam paragraf dengan lebih rapi dan alami, namun tetap menjaga macam kata yang keluar tetap sedikit sehingga aman dari risiko halusinasi.

------------------------------------------------------

# Experiment 2 - TOP_K

## TOP_K = 1

### Actual Output

#### Pertanyaan 1

**Steps in the first pass (≈5‑10 minutes)**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings, ignoring the rest of the text.  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.  

These steps are taken from **HowtoReadPaper.pdf, page 1**.

The document mentions that after this first pass you should be able to answer “the five Cs,” but the list of those five Cs is not included in the provided excerpt. Therefore, the specific five Cs cannot be retrieved from the uploaded material.

#### Pertanyaan 2

The uploaded document only mentions that the first pass of the three‑pass approach gives a general idea about the paper; it does not provide the complete list of the three steps. Therefore, the answer was not found in the uploaded documents.

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6149765955892066
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    }
  ]

### Observation

### Observation

*   **Pertanyaan 1**: Dengan 1 *chunk* paling atas dari halaman 1 yakni `score: 0.61497`, LLM sudah bisa menjawab 4 langkah *first pass* dengan tepat, namun gagal menjawab daftar "Five Cs" karena rinciannya terpotong ke *chunk* lain.
*   **Pertanyaan 2**: Sistem **gagal menjawab pertanyaan** dengan menampilkan *"the answer was not found in the uploaded documents"*. Hal ini terjadi karena 1 *chunk* dengan nilai tertinggi yakni `score: 0.79597` di halaman 1 hanya berisi kalimat pengantar di bagian *Introduction* yakni *"This paper describes the 'three-pass' approach and its use in doing a literature survey"* , sedangkan penjelasan langkah-langkah *literature survey* yang sebenarnya berada di halaman 2 dan tidak ikut terbawa karena batas `TOP_K = 1`.

------------------------------------------------------

## TOP_K = 4

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1):**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings (ignore the rest of the text).  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.

**Five “Cs”** – The document states that after the first pass you should be able to answer “the five Cs,” but the list of those Cs is not included in the uploaded pages. Therefore the answer to that part was not found in the provided documents.

#### Pertanyaan 2

The three‑pass method suggests the following three steps when you conduct a literature survey:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to locate three‑to‑five recent papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **Do a first pass on each paper** – read each paper quickly (title, abstract, introduction, section headings, conclusions, and skim figures/tables) to obtain a general sense of its content and contributions.【HowtoReadPaper.pdf | Page 1】

3. **Read the related‑work sections** – after the first pass, examine the papers’ related‑work sections to identify implicit assumptions, missing citations, and potential methodological issues, which helps you map the field and spot gaps.【HowtoReadPaper.pdf | Page 2】

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6149765955892066
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6995426958218204
    }
  ]

### Observation

*   **Pertanyaan 1**: Hasil jawaban dan sumber yakni `page: 1`, `score: 0.61497` tetap sama seperti `TOP_K = 1` dimana 4 langkah terjawab, "Five Cs" belum ketemu.
*   **Pertanyaan 2**: Terjadi **perbaikan mutu jawaban yang sangat besar** dibanding saat `TOP_K = 1`. Dengan memperbesar pengambilan menjadi 4 *chunk*, sistem sekarang berhasil membawa konteks dari **halaman 2**, dengan `score: 0.69954`, selain halaman 1, dengan `score: 0.79597`. Hasilnya, LLM berhasil mengekstrak dan menyusun 3 langkah pelaksanaan *literature survey* yakni mencari 3–5 *paper* di Google Scholar/CiteSeer, melakukan *first pass*, dan membaca bagian *related work*.

------------------------------------------------------

## TOP_K = 8

### Actual Output

#### Pertanyaan 1

**Steps in the first pass (≈5‑10 minutes)**  

1. Carefully read the **title**, **abstract**, and **introduction**.  
2. Read the **section and sub‑section headings** (ignore the body text).  
3. Read the **conclusions**.  
4. Glance over the **references**, mentally noting any you have already read.  

*(Source: HowtoReadPaper.pdf, p. 1)*  

**The five “Cs”** that you should be able to answer after this pass are not listed in the provided excerpts, so the answer was not found in the uploaded documents.

#### Pertanyaan 2

The three‑step procedure for a literature survey using the three‑pass method is:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to locate three‑to‑five current papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **Do a first pass on each paper** – quickly scan each one (title, abstract, headings, figures, conclusions) to get a bird’s‑eye view and decide whether it merits deeper reading.【HowtoReadPaper.pdf | Page 1】

3. **Read the related‑work sections** – after the first pass, examine the related‑work portions of those papers to identify assumptions, missing citations, and potential issues, which helps you map the field and spot gaps for your own survey.【HowtoReadPaper.pdf | Page 2】

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6149765955892066
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6995426958218204
    }
  ]

### Observation

*   **Pertanyaan 1**: Jawaban faktual dan referensi halaman yakni `page: 1`, `score: 0.61497` tetap sama dengan `TOP_K = 1` dan `TOP_K = 4`; daftar "Five Cs" masih belum terjawab.
*   **Pertanyaan 2**: Daftar sumber dimana `page: 1` dengan `0.79597` dan `page: 2` dengan `0.69954` serta isi materi ketiga langkah yang dikeluarkan hampir identik dengan `TOP_K = 4`, hanya ada sedikit perbedaan kata seperti istilah *"bird's-eye view"* pada poin ke-2. Mengalikan dua `TOP_K` dari 4 ke 8 tidak menambah informasi baru yang penting ke dalam jawaban akhir atau mengalami *diminishing returns*.

------------------------------------------------------

## Kesimpulan Experiment TOP_K

Apakah TOP_K yang lebih besar selalu menghasilkan jawaban yang lebih baik?

Tidak selalu. Menaikkan `TOP_K` dari `1` ke `4` memang krusial untuk memperbaiki kegagalan pada Pertanyaan 2 karena pada `TOP_K = 1`, urutan pertama ditempati oleh kalimat pengantar di halaman 1 yang tidak berisi jawaban, sedangkan isi jawaban sebenarnya ada di halaman 2 dengan nilai `0.69954`. Namun, ketika `TOP_K` dinaikkan lebih lanjut dari `4` ke `8`, mutu jawaban pada Pertanyaan 1 maupun Pertanyaan 2 tidak naik lagi, dan justru hanya memperbanyak jumlah *token* konteks yang dikirim ke LLM.

Menurut kalian TOP_K mana yang paling cocok untuk PDF yang digunakan?

`TOP_K = 4`.

Kenapa?

Karena `TOP_K = 1` terbukti terlalu sempit dan berisiko gagal ketika kalimat pengantar/abstrak punya *similarity score* lebih tinggi daripada paragraf isi seperti pada Pertanyaan 2. Sebaliknya, `TOP_K = 4` sudah cukup lebar untuk mengambil konteks lintas halaman yakni halaman 1 dan halaman 2 sehingga Pertanyaan 2 terjawab dengan baik, tanpa membuang kuota *token* secara berlebihan seperti pada `TOP_K = 8`.

------------------------------------------------------

# Experiment 3 - Chunk Size

Gunakan:

```text
CHUNK_OVERLAP = 20
```

untuk seluruh percobaan.

------------------------------------------------------

## Chunk Size = 50

### Chunks Stored

77 chunks indexed

### Actual Output

#### Pertanyaan 1

**First‑pass steps** (HowtoReadPaper.pdf, p. 1)  
1. Read the **title**, **abstract** and **introduction**.  
2. Skim the **section headings**, **figures/tables** and any highlighted text.  
3. Read the **conclusions**.  
4. Glance over the **references**, noting any you already know.

**The five “C’s” you should be able to answer after this pass** (p. 1)  

1. **Category** – What type of paper is it? (e.g., algorithm, system, theory)  
2. **Context** – Where does it fit within the larger field?  
3. **Correctness** – Do the results appear to be valid?  
4. **Contributions** – What are the main contributions?  
5. **Clarity** – Is the paper well‑written and understandable?

#### Pertanyaan 2

The answer was not found in the uploaded documents.

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6489539002726534
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.5626978882520279
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.8497848189399766
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.7267146094920708
    }
  ]

### Observation

*   Jumlah potongan yang tersimpan naik sangat banyak menjadi **77 chunks** yakni lebih dari dua kali lipat dibanding `CHUNK_SIZE = 100`.
*   **Pertanyaan 1**: *Similarity score* naik ke `0.64895` pada halaman 1 dan ikut membawa konteks tambahan dari halaman 2 yakni `0.56269`. Namun, karena potongan teks terlalu pendek, terjadi **perubahan isi karena potongan terlalu kecil atau distorsi konteks** dimana langkah ke-2 menyebutkan *"figures/tables"* yang sebenarnya merupakan langkah *second pass*, dan daftar rincian contoh pada "Five Cs" seperti *algorithm, system, theory* berasal dari ingatan bawaan LLM sendiri karena teks asli PDF terpotong.
*   **Pertanyaan 2**: Walaupun memberikan ***similarity score* paling tinggi** di antara semua percobaan dimana `0.84978` di halaman 1 dan `0.72671` di halaman 2, LLM malah **gagal menjawab pertanyaan** dengan menampilkan *"The answer was not found in the uploaded documents"*. Hal ini terjadi karena ukuran 50 *token* memisahkan kalimat pengantar Bab 3 dengan menampilkan *"Here is how you can use the three-pass approach to help"* dari paragraf isi langkah-langkahnya. Kuota `TOP_K = 4` habis terisi oleh potongan-potongan kalimat pengantar yang penuh kata kunci tetapi tidak punya isi penjelasan.

------------------------------------------------------

## Chunk Size = 100

### Chunks Stored

34 chunks indexed

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1):**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings (ignore the rest of the text).  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.

**Five “Cs”** – The document states that after the first pass you should be able to answer “the five Cs,” but the list of those Cs is not included in the uploaded pages. Therefore the answer to that part was not found in the provided documents.

#### Pertanyaan 2

The three‑pass method suggests the following three steps when you conduct a literature survey:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to locate three‑to‑five recent papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **Do a first pass on each paper** – read each paper quickly (title, abstract, introduction, section headings, conclusions, and skim figures/tables) to obtain a general sense of its content and contributions.【HowtoReadPaper.pdf | Page 1】

3. **Read the related‑work sections** – after the first pass, examine the papers’ related‑work sections to identify implicit assumptions, missing citations, and potential methodological issues, which helps you map the field and spot gaps.【HowtoReadPaper.pdf | Page 2】

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6149765955892066
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6995426958218204
    }
  ]

### Observation

*   Jumlah potongan yang tersimpan berkurang menjadi **34 chunks**.
*   **Pertanyaan 1**: Pengambilan data atau *retrieval* lebih fokus pada halaman 1 dimana `score: 0.61497`. Keempat langkah *first pass* terjawab dengan akurat sesuai teks sumber, namun batas 100 *token* memotong teks pas setelah kalimat pengantar *"answer the five Cs"*. Akibatnya, rincian kelima poin C tidak ikut terbawa.
*   **Pertanyaan 2**: Walaupun *similarity score* sedikit turun yakni `0.79597` di halaman 1 dan `0.69954` di halaman 2, pertanyaan sekarang **berhasil dijawab dalam 3 poin**. Kapasitas 100 *token* membuat kalimat pembuka Bab 3 tetap menyatu dengan paragraf langkah pertama yakni pencarian 3–5 *paper* di Google Scholar/CiteSeer, melakukan *first pass*, dan membaca bagian *related work*.

------------------------------------------------------

## Chunk Size = 120

### Chunks Stored

28 chunks indexed

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1)**  
1. Carefully read the **title, abstract, and introduction**.  
2. Read the **section and sub‑section headings** (ignore the body text).  
3. Read the **conclusions**.  
4. Glance over the **references**, mentally noting any you have already read.  

**The “five Cs” you should be able to answer after the first pass**  
- **Category** – what type of paper it is (e.g., measurement paper, analysis of an existing system, description of a research prototype).  

The remaining four Cs are not listed in the uploaded document, so their details were not found in the provided context.

#### Pertanyaan 2

**Three steps for a literature survey with the three‑pass approach**

1. **Find a small set of recent papers** – Use an academic search engine (e.g., Google Scholar, CiteSeer) and appropriate keywords to locate 3‑5 current papers in the target area. 【HowtoReadPaper.pdf, p. 2】

2. **Do the first pass on each paper** – Skim each paper to get a general sense of its contribution, then read its *Related Work* section. This gives you a “thumbnail” summary of the recent work and may point you to a dedicated survey paper. 【HowtoReadPaper.pdf, p. 2】

3. **Decide the next action** – After the first pass you can (a) set the paper aside, (b) return later after gaining background knowledge, or (c) continue to the third pass (a full, detailed read and virtual re‑implementation) if you need deep understanding. 【HowtoReadPaper.pdf, p. 2‑3】

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6223293897275901
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7850123358226336
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6940980289141198
    }
  ]

### Observation

*   Jumlah potongan yang tersimpan mengecil menjadi **28 chunks** karena tiap *chunk* menampung lebih banyak *token*.
*   **Pertanyaan 1**: *Similarity score* di halaman 1 naik ke `0.62232`. Tambahan 20 *token* terbukti memperluas batas akhir *chunk* sehingga tidak hanya berisi 4 langkah *first pass*, tetapi juga berhasil mengambil **poin pertama dari Five Cs (`Category`)** secara pas sesuai teks asli PDF seperti *"measurement paper, analysis of an existing system, description of a research prototype"*.
*   **Pertanyaan 2**: *Similarity score* berada pada `0.78501` di halaman 1 dan `0.69409` di halaman 2. Karena ukuran *chunk* lebih lebar, rincian paragraf pertama Bab 3 terbawa lebih lengkap hingga mencakup penjelasan mengenai *"thumbnail summary of the recent work"* dan *"pointer to a recent survey paper"*, sedangkan poin ke-3 diambil dari potongan akhir Sub-bab 2.2 mengenai tiga pilihan keputusan setelah membaca *paper*.

------------------------------------------------------

## Kesimpulan Experiment Chunk Size

Apa hubungan Chunk Size dengan jumlah chunk yang tersimpan?

Berbanding terbalik. Semakin kecil nilai `CHUNK_SIZE`, semakin banyak jumlah potongan atau `chunks_stored` yang dikeluarkan dari dokumen yang sama dimana `CHUNK_SIZE = 50` menghasilkan **77 chunks**, `100` menghasilkan **34 chunks**, dan `120` menghasilkan **28 chunks**.

Apakah chunk yang lebih kecil selalu menghasilkan retrieval yang lebih baik?

Tidak. Percobaan pada Pertanyaan 2 membuktikan bahwa `CHUNK_SIZE = 50` memberikan *similarity score* tertinggi yakni `0.84978`, tetapi justru gagal total memberikan jawaban *"The answer was not found"*. Potongan yang terlalu kecil memisahkan kalimat judul/pengantar dari isi penjelasannya. Kalimat pengantar tersebut menguasai nilai kemiripan vektor dan menghabiskan kuota `TOP_K`, sehingga isi materi yang sebenarnya tidak terbawa.

Menurut kalian Chunk Size mana yang paling cocok?

`CHUNK_SIZE = 120`.

Kenapa?

Karena pada `CHUNK_SIZE = 120`, potongan teks cukup lebar untuk menjaga keutuhan kalimat pengantar beserta rincian isinya di dalam satu *chunk*. Pengaturan ini berhasil menjawab Pertanyaan 1 dengan paling tepat yakni 4 langkah *first pass* dan poin pertama *Five Cs* sesuai teks asli tanpa mengarang cerita sekaligus mengambil rincian paragraf *Literature Survey* yang lebih lengkap pada Pertanyaan 2 dengan jumlah penyimpanan paling hemat tempat yakni 28 *chunks*.

------------------------------------------------------

# Experiment 4 - Chunk Overlap

Gunakan:

```text
CHUNK_SIZE = 100
```

untuk seluruh percobaan.

------------------------------------------------------

## Chunk Overlap = 0

### Chunks Stored

34 chunks indexed

### Actual Output

#### Pertanyaan 1

**Steps in the first pass (HowtoReadPaper.pdf, p. 1)**  
1. Carefully read the **title**, **abstract**, and **introduction**.  
2. Read the **section and sub‑section headings** only, ignoring the rest of the text.  
3. Read the **conclusions**.  
4. Glance over the **references**, mentally noting any you have already read.

**Five Cs** – The document states that after the first pass you should be able to answer “the five Cs,” but the specific Cs are not listed in the provided excerpts. Therefore, the answer to that part was not found in the uploaded documents.

#### Pertanyaan 2

The three‑step way to run a literature survey with the three‑pass method is:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar, CiteSeer) and well‑chosen keywords to locate 3‑5 papers in the target area【HowtoReadPaper.pdf | Page 2】.  
2. **Do a first pass on each paper** – read the title, abstract, introduction and conclusion to get a quick, general sense of what each work is about【HowtoReadPaper.pdf | Page 1】.  
3. **Read the related‑work sections** – after the first pass, examine the papers’ related‑work sections to spot implicit assumptions, missing citations, and possible methodological issues【HowtoReadPaper.pdf | Page 2】.

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6642873483940964
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6995426958218204
    }
  ]

### Observation

*   Jumlah potongan yang tersimpan tetap **34 chunks**, sama dengan `CHUNK_OVERLAP = 20`. Hal ini terjadi karena `RecursiveCharacterTextSplitter` lebih mengutamakan pemotongan pada batas paragraf alami terlebih dahulu.
*   **Pertanyaan 1**: *Similarity score* pada halaman 1 naik ke `0.66428`, lebih tinggi dibanding `0.61497` pada `CHUNK_OVERLAP = 20`, karena potongan teks langkah *first pass* tidak tercampur *token* dari paragraf lain. Empat langkah terjawab dengan akurat, namun daftar "Five Cs" tetap terpisah di *chunk* lain.
*   **Pertanyaan 2**: *Similarity score* berada pada `0.79597` di halaman 1 dan `0.69954` di halaman 2. Ketiga langkah berhasil disusun, namun pada langkah ke-3 masih terbawa kalimat dari akhir Sub-bab 2.3 seperti *"spot implicit assumptions, missing citations, and possible methodological issues"* yang menempel pada *chunk* yang sama.

------------------------------------------------------

## Chunk Overlap = 20

### Chunks Stored

34 chunks indexed

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1):**  
1. Carefully read the title, abstract, and introduction.  
2. Read the section and sub‑section headings (ignore the rest of the text).  
3. Read the conclusions.  
4. Glance over the references, mentally noting any you have already read.

**Five “Cs”** – The document states that after the first pass you should be able to answer “the five Cs,” but the list of those Cs is not included in the uploaded pages. Therefore the answer to that part was not found in the provided documents.

#### Pertanyaan 2

The three‑pass method suggests the following three steps when you conduct a literature survey:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar, CiteSeer) with well‑chosen keywords to locate three‑to‑five recent papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **Do a first pass on each paper** – read each paper quickly (title, abstract, introduction, section headings, conclusions, and skim figures/tables) to obtain a general sense of its content and contributions.【HowtoReadPaper.pdf | Page 1】

3. **Read the related‑work sections** – after the first pass, examine the papers’ related‑work sections to identify implicit assumptions, missing citations, and potential methodological issues, which helps you map the field and spot gaps.【HowtoReadPaper.pdf | Page 2】

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6149765955892066
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6995426958218204
    }
  ]

### Observation

*   Jumlah potongan yang tersimpan adalah **34 chunks**.
*   **Pertanyaan 1**: *Similarity score* di halaman 1 sedikit turun ke `0.61497` akibat adanya tumpang tindih atau irisan 20 *token* antar-*chunk*, namun isi materi atau substansi jawaban tetap identik yaitu 4 langkah terjawab dan "Five Cs" tidak ketemu.
*   **Pertanyaan 2**: *Similarity score* `0.79597` di halaman 1 dan `0.69954` di halaman 2 serta isi jawaban sama dengan `CHUNK_OVERLAP = 0`, di mana langkah ke-3 masih berisi pencampuran konteks dari akhir Sub-bab 2.3.

------------------------------------------------------

## Chunk Overlap = 40

### Chunks Stored

38 chunks indexed

### Actual Output

#### Pertanyaan 1

**First‑pass steps (HowtoReadPaper.pdf, p. 1)**  
1. Carefully read the **title**, **abstract**, and **introduction**.  
2. Read the **section and sub‑section headings** only, ignoring the rest of the text.  
3. Read the **conclusions**.  
4. Glance over the **references**, mentally noting any you have already read.

**Five “Cs”** – The document states that after the first pass you should be able to answer the “five Cs,” but the list of those five items is not included in the uploaded pages. Therefore the specific five Cs cannot be retrieved from the provided context.

#### Pertanyaan 2

The literature‑survey workflow described in the paper consists of three concrete steps:

1. **Find a small set of recent papers** – use an academic search engine (e.g., Google Scholar or CiteSeer) with well‑chosen keywords to locate 3–5 current papers in the target area.【HowtoReadPaper.pdf | Page 2】

2. **Do a first pass on each paper** – skim each paper (title, abstract, introduction, figures, conclusions, etc.) to obtain a quick sense of what the work is about.【HowtoReadPaper.pdf | Page 2】

3. **Read the related‑work sections** – after the initial skim, examine the “Related Work” (or bibliography) of those papers to discover additional relevant studies and to map the broader research landscape.【HowtoReadPaper.pdf | Page 2】

### Sources / Similarity Score

#### Pertanyaan 1

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.6642873483940964
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.5762787258267388
    }
  ]

#### Pertanyaan 2

"sources": [
    {
      "source": "HowtoReadPaper.pdf",
      "page": 1,
      "score": 0.7959770474312893
    },
    {
      "source": "HowtoReadPaper.pdf",
      "page": 2,
      "score": 0.6995426958218204
    }
  ]

### Observation

*   Jumlah potongan yang tersimpan naik menjadi **38 chunks** karena jumlah tumpang tindih mencapai 40% dari `CHUNK_SIZE = 100`.
*   **Pertanyaan 1**: *Similarity score* halaman 1 berada di `0.66428`, namun sistem juga ikut membawa konteks tambahan dari halaman 2 yakni `score: 0.57627` tanpa berhasil memperlihatkan rincian "Five Cs".
*   **Pertanyaan 2**: *Similarity score* paling tinggi per halaman tetap `0.79597` di halaman 1 dan `0.69954` di halaman 2, tetapi **mutu isi langkah ke-3 naik secara besar**. Pergeseran titik potong pada 38 *chunks* membuat konteks Bab 3 tidak lagi tercampur oleh kalimat akhir Sub-bab 2.3 dengan menampilkan *"implicit assumptions..."*. Sekarang, sistem secara akurat menyebutkan pemeriksaan *"Related Work (or bibliography) of those papers to discover additional relevant studies"* dengan semua kutipan langkah ke-1 hingga ke-3 merujuk pas ke `Page 2`.

------------------------------------------------------

## Kesimpulan Experiment Chunk Overlap

Apa pengaruh Chunk Overlap yang kalian lihat?

1.  **Mengubah Jumlah Chunk dan Titik Potong**: Menaikkan `CHUNK_OVERLAP` ke `40` menambah jumlah `chunks_stored` dari 34 menjadi 38 *chunks* dan menggeser posisi pemotongan antar-paragraf.
2.  **Menjaga Sambungan Konteks Antar-Bagian**: Pada Pertanyaan 2, `CHUNK_OVERLAP = 40` berhasil memperbaiki isi langkah ke-3 sehingga murni merangkum isi Bab 3 yakni *Related Work / bibliography* di halaman 2 tanpa tercampur kalimat penutup dari Sub-bab 2.3.
3.  **Naik-Turun Nilai & Pengulangan Data**: Pada Pertanyaan 1, perubahan *overlap* mengubah nilai kemiripan atau *similarity score*, yaitu dari `0.66428` menjadi `0.61497`, dan pada nilai `40` ikut membawa *chunk* halaman 2 dengan skor `0.57627` yang tidak diperlukan untuk menjawab langkah *first pass*.

Apakah overlap yang lebih besar selalu menghasilkan jawaban yang lebih baik?

Tidak selalu untuk setiap pertanyaan. Untuk Pertanyaan 2, `CHUNK_OVERLAP = 40` memang mengeluarkan jawaban yang paling bersih dari pencampuran sub-bab. Namun untuk Pertanyaan 1, `CHUNK_OVERLAP = 40` tetap gagal memunculkan daftar "Five Cs" dan justru membawa informasi sampah atau *noise* dari halaman 2 serta memperbanyak jumlah *chunk* yang harus disimpan di *database*.

Menurut kalian nilai mana yang paling cocok?

`CHUNK_OVERLAP = 20` jika dipasangkan dengan `CHUNK_SIZE = 120`, atau `CHUNK_OVERLAP = 40` jika ukuran `CHUNK_SIZE` dikunci pada `100` dan prioritas utama yang paling penting adalah ketepatan pemisahan sub-bab pada Pertanyaan 2. Secara umum, `CHUNK_OVERLAP = 20` adalah titik tengah yang paling hemat tempat karena menjaga jumlah *chunk* tetap ramping yakni 34 *chunks* tanpa membawa *noise* lintas halaman pada Pertanyaan 1.

------------------------------------------------------

# Final Configuration

Setelah seluruh eksperimen, pilih konfigurasi yang menurut kalian menghasilkan hasil terbaik untuk PDF yang digunakan.

```text
Temperature:
TOP_K:
Chunk Size:
Chunk Overlap:
```

```text
Temperature: 0.2
TOP_K: 4
Chunk Size: 120
Chunk Overlap: 20
```

------------------------------------------------------

# Final Questions

### 1. Parameter mana yang paling terasa memengaruhi hasil aplikasi kalian?

`CHUNK_SIZE` dan `TOP_K`. Pada Pertanyaan 2, mengecilkan `CHUNK_SIZE` menjadi `50` atau menurunkan `TOP_K` menjadi `1` langsung membuat sistem gagal total menjawab pertanyaan dengan menampilkan *"The answer was not found in the uploaded documents"*. Sebaliknya, menaikkan `CHUNK_SIZE` ke `120` dan `TOP_K` ke `4` membuat kedua pertanyaan bisa dijawab dengan rincian yang jauh lebih lengkap.

### 2. Apakah Temperature memengaruhi Retrieval atau Generation? Jelaskan.

`Temperature` hanya berpengaruh pada tahap **Generation**, bukan *Retrieval*. Saat `temperature` diubah dari `0.0`, `0.2`, hingga `0.8`, Qdrant tetap mengambil *chunk* dan *similarity score* yang sama persis. Perubahan `temperature` hanya memengaruhi cara LLM memilih kata atau *token* untuk menyusun kalimat dan mengelompokkan poin jawaban seperti perbedaan cara LLM membagi 3 langkah *literature survey* pada Pertanyaan 2 antara `temperature = 0.0` dan `0.2`.

### 3. Apakah TOP_K yang lebih besar selalu menghasilkan jawaban yang lebih baik?

Tidak selalu. Menaikkan `TOP_K` dari `1` ke `4` memang sangat memperbaiki hasil Pertanyaan 2 mulai dari tidak terjawab menjadi terjawab lengkap karena berhasil membawa *chunk* halaman 2. Namun, ketika dinaikkan lagi dari `4` ke `8`, hasil pada Pertanyaan 1 maupun Pertanyaan 2 tidak mengalami penambahan mutu lebih lanjut atau disebut *diminishing returns*.

### 4. Apa yang terjadi ketika Chunk Size dibuat lebih kecil?

Ketika `CHUNK_SIZE` diperkecil menjadi `50`:
1. Jumlah potongan yang disimpan membengkak lebih dari dua kali lipat yakni dari 34 menjadi **77 chunks**.
2. Pada Pertanyaan 1, isi materi yang terpotong terlalu pendek membuat LLM mencampuradukkan langkah *first pass* dengan *second pass* atau disebut *"skim figures/tables"* dan menambal contoh "Five Cs" memakai ingatan bawaannya sendiri.
3. Pada Pertanyaan 2, walaupun *similarity score* mencapai angka tertinggi yakni `0.84978`, sistem **gagal menjawab pertanyaan** karena kalimat pengantar yang pendek terpisah dari paragraf penjelasannya dan menghabiskan semua kuota `TOP_K = 4`.

### 5. Setelah melakukan eksperimen, apa fungsi Chunk Overlap menurut pemahaman kalian?

`CHUNK_OVERLAP` berguna menjaga sambungan konteks di perbatasan antar-*chunk* agar informasi yang terpotong di ujung suatu *chunk* tetap punya hubungan di *chunk* berikutnya. Pada Pertanyaan 2, perubahan `CHUNK_OVERLAP` ke `40` terbukti menggeser batas potongan sehingga langkah ke-3 pada Bab 3 tidak lagi tercampur dengan kalimat penutup dari Sub-bab 2.3.

### 6. Kenapa perubahan Chunk Size dan Chunk Overlap membutuhkan ingestion ulang?

Karena `CHUNK_SIZE` dan `CHUNK_OVERLAP` bekerja pada tahap **Ingestion** (`PDF -> Chunking -> Embedding -> Qdrant`). Keduanya menentukan bagaimana teks PDF dipotong dan diubah menjadi *vektor* sebelum disimpan ke *database* Qdrant. Tanpa menghapus `qdrant_data/` dan melakukan proses pemasukan data atau *ingestion* ulang, aplikasi hanya akan membaca potongan *chunk* lama yang sudah disimpan sebelumnya.

### 7. Kenapa perubahan Temperature tidak membutuhkan ingestion ulang?

Karena `Temperature` adalah parameter **LLM Generation** yang baru dipakai saat mengirim *prompt* dan konteks hasil pencarian ke API Groq. Mengubah `temperature` sama sekali tidak mengubah potongan teks maupun *vector embedding* yang ada di Qdrant.

### 8. Menurut kalian, apakah ada satu konfigurasi RAG yang akan selalu paling bagus untuk semua jenis dokumen?

Tidak ada. Pengaturan atau konfigurasi terbaik sangat bergantung pada susunan dokumen dan sifat dari pertanyaan. Bahkan di dalam satu dokumen pendek yang sama, yakni `HowtoReadPaper.pdf`, Pertanyaan 1 butuh `CHUNK_SIZE` yang lebih lebar, setidaknya `>= 120`, agar daftar "Five Cs" tidak terpotong dari sub-bab *first pass*, sedangkan Pertanyaan 2 sangat bergantung pada `TOP_K >= 4` dan `CHUNK_OVERLAP` agar kalimat pengantar di halaman 1 tidak menutupi isi penjelasan di halaman 2.

------------------------------------------------------

# Personal Reflection

### Bagian eksperimen mana yang hasilnya paling berbeda dari dugaan kalian?

Hasil pada **Percobaan 3 yakni `CHUNK_SIZE = 50` untuk Pertanyaan 2**. Awalnya saya mengira semakin tinggi *similarity score*, maka jawaban yang dikeluarkan pasti semakin bagus. Ternyata pada `CHUNK_SIZE = 50`, walaupun Pertanyaan 2 mendapatkan *similarity score* paling tinggi di semua percobaan yakni `0.84978`, LLM malah tidak bisa menjawab sama sekali karena potongan 50 *token* hanya mengambil kalimat-kalimat pengantar pendek tanpa berisi isi penjelasannya.

### Parameter mana yang awalnya kalian anggap tidak terlalu penting tetapi ternyata berpengaruh?

`CHUNK_SIZE` dan hubungannya dengan `TOP_K`. Percobaan ini memperlihatkan bahwa angka *similarity score* yang tinggi pada `TOP_K = 1` yakni `0.79597` di halaman 1 bisa menipu kalau ukuran *chunk* memisahkan kalimat topik dari paragraf penjelasannya.

### Setelah mengerjakan tugas ini, bagaimana kalian menjelaskan hubungan antara Retrieval dan Generation pada RAG?

**Retrieval** menentukan batas ketersediaan dan keutuhan data nyata lewat pengaturan *chunking* dan `TOP_K`, sedangkan **Generation** bertugas merangkai dan memperlihatkan data tersebut sesuai perintah, dengan pengaturan `temperature`. Jika tahap *Retrieval* gagal mengambil potongan yang lengkap seperti pada `TOP_K = 1` atau `CHUNK_SIZE = 50` di Pertanyaan 2, maka tahap *Generation* tidak akan bisa mengeluarkan jawaban yang benar.

### Jika aplikasi ini dikembangkan lebih lanjut, parameter atau bagian apa lagi yang ingin kalian coba?

1. Mencoba `CHUNK_SIZE` yang lebih besar yakni `200`–`250` *token* agar semua rincian "Five Cs" di halaman 1 dan ketiga paragraf *Literature Survey* di halaman 2 bisa diambil secara lengkap tanpa terpotong.
2. Menambahkan fitur **Reranker** atau *Cross-Encoder* setelah pengambilan `TOP_K` dari Qdrant agar potongan paragraf yang berisi penjelasan mendalam mendapat urutan utama yang lebih tinggi dibanding kalimat pengantar singkat di abstrak/pendahuluan.
3. Memajang isi teks dari setiap *chunk* yang terbawa pada layar tampilan web untuk mempermudah pengecekan dan pencarian eror atau *debugging* jalur data RAG.

------------------------------------------------------

# AI Usage

### AI tools yang digunakan

Google Gemini dan Groq API (`openai/gpt-oss-120b` pada aplikasi RAG).

### AI digunakan untuk membantu bagian apa?

Membantu menjelaskan langkah-langkah teknis percobaan, penggunaan *endpoint* `/docs` untuk melihat *similarity score*, serta cara *reset* `qdrant_data/`.

### Bagian eksperimen mana yang kalian lakukan dan evaluasi sendiri?

*   Menjalankan server aplikasi RAG secara lokal di komputer sendiri dan mengunggah dokumen `HowtoReadPaper.pdf`.
*   Mengubah semua aturan atau parameter mulai dari `temperature`, `TOP_K`, `CHUNK_SIZE`, dan `CHUNK_OVERLAP`, melakukan *reset database* vektor serta proses memasukkan data ulang atau *re-ingestion*.
*   Menjalankan kedua pertanyaan pengujian di setiap contoh kasus, serta mengumpulkan semua data aktual, seperti `Actual Output`, `Chunks Stored`, dan `Sources / Similarity Score`.

------------------------------------------------------

# Pengumpulan

Project **wajib dikumpulkan dalam bentuk repository GitHub**.

Repository awal berasal dari:

```text
https://github.com/arifian853/rag-app
```

Setelah selesai melakukan eksperimen, buat repository kalian sendiri dengan nama:

```text
tugas-rag-experiment
```

------------------------------------------------------

## Ganti Remote Repository

Buat repository baru di GitHub terlebih dahulu.

Kemudian dari folder project:

```bash
git remote set-url origin https://github.com/USERNAME/tugas-rag-experiment.git
```

Pastikan remote sudah berubah:

```bash
git remote -v
```

Kemudian:

```bash
git add .
git commit -m "Submit RAG Parameter Exploration"
git push -u origin master
```

Jika branch repository kalian menggunakan `main`, sesuaikan perintah push:

```bash
git push -u origin main
```

------------------------------------------------------

# Yang Perlu Di-push

Source code project tetap boleh ikut di repository.

README hasil eksperimen **wajib tersedia**.

Pastikan `.env` tidak ikut ter-upload.

Folder berikut juga tidak perlu di-push:

```text
venv/
qdrant_data/
data/uploads/
__pycache__/
```

------------------------------------------------------

# Sebelum Mengumpulkan

Pastikan:

- Aplikasi berhasil dijalankan.
- PDF berhasil di-ingest.
- Pertanyaan berhasil dijawab.
- Experiment Temperature selesai.
- Experiment TOP_K selesai.
- Experiment Chunk Size selesai.
- Experiment Chunk Overlap selesai.
- Actual output berasal dari aplikasi yang benar-benar dijalankan.
- Similarity score berasal dari aplikasi.
- Jumlah `chunks_stored` dicatat dari hasil ingestion.
- Qdrant di-reset saat mengganti parameter chunking.
- README sudah diisi.
- Final Configuration sudah dipilih.
- Final Questions sudah dijawab.
- Personal Reflection sudah dijawab.
- `.env` tidak masuk repository.

------------------------------------------------------

# Yang Dikumpulkan

**Kumpulkan LINK REPOSITORY GITHUB di LMS.**

Contoh:

```text
https://github.com/username/tugas-rag-experiment
```

Yang dikumpulkan hanya:

**Link Repository GitHub**

------------------------------------------------------

**Deadline:**

Minggu, 1 November 2026, 23.59 WIB

Selamat bereksperimen!