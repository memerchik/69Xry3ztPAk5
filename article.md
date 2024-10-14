---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.14.4
  kernelspec:
    display_name: R
    language: R
    name: ir
---

<!-- #region tags=["title"] -->
# Shaping the Transnational Public Sphere in Republican China: Discourses and Practices of the Rotary Club in the Shanghai Press (1919-1949)
<!-- #endregion -->

<!-- #region tags=["contributor"] -->
### Cécile  Armand [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0002-9107-6443)
Ecole Normale Supérieure de Lyon
<!-- #endregion -->

<!-- #region tags=["copyright"] -->
[![cc-by-nc-nd](https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/)
©<Cécile ARMAND>. Published by De Gruyter in cooperation with the University of Luxembourg Centre for Contemporary and Digital History. This is an Open Access article distributed under the terms of the [Creative Commons Attribution License CC-BY-NC-ND](https://creativecommons.org/licenses/by-nc-nd/4.0/)
<!-- #endregion -->

<!-- #region tags=["disclaimer"] -->
This research has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No 788476), the Chiang Ching-kuo Foundation for International Scholarly Exchange (Project n°RG004-U-21) and the French National Research Agency (ANR-23-AERC-0018).
<!-- #endregion -->

<!-- #region tags=["keywords"] -->
elites, geographical information system (GIS), historical newspapers, modern China, named entity recognition (NER), network analysis, Sino-American relations, topic modeling
<!-- #endregion -->

<!-- #region tags=["abstract"] -->
This article focuses on the Rotary Club as a case study and employs the periodical press as its primary source to reinvigorate past discussions regarding the public sphere and transnationalism in Republican China (1912-1949). Utilizing newly accessible digitized newspapers in both Chinese and English, and incorporating various computational methods such as topic modeling, Named Entity Recognition (NER), Geographic Information System (GIS), and network analysis, the author investigates how the Rotary Club, functioning as a transnational elite organization, strategically utilized the periodical press to promote its activities and present itself as a public-spirited entity committed to social welfare and international peace. This mixed-method approach reveals a public facade of unity and social harmony, which sharply contrasts with the narrative of language politics and internal tensions found in archival records. From a bilingual perspective, the English press emphasized the political dimensions of the public, expressed through terms like public opinion and manifested through official speeches or academic lectures. On the other hand, the Chinese press took a more pragmatic stance, concentrating on fundraising campaigns and educational reforms, and expressing concerns about the public welfare (*gongyi* 公益) of the general population (*gongzhong* 公眾). While both presses focused on the Pacific area, English periodicals paid more attention to foreign communities in China, their homelands, and colonial empires. In contrast, the Chinese press highlighted figures of Chinese border-crossers and overseas Chinese communities in southeast Asia and America. These differences are indicative of distinct reader interests and the access of newspaper editors to different sources of information. Journalistic content and practices converged during the 1930s but diverged again during the war and post-war periods. Methodologically, this paper contributes a robust methodology for utilizing digitized newspapers in historical research, viewing computational methods not as a replacement but as an aid for more efficient close reading and hermeneutics. Ultimately, the author advocates for increased collaboration with computer scientists to enhance data quality upstreams, allowing researchers to focus more effectively on the crucial tasks of analysis and interpretation.
<!-- #endregion -->

## Introduction

<!-- #region citation-manager={"citations": {"": []}} -->
> *The Chinese people had developed, the speaker quoted Dr. Wang as stating, the solidarity of family life. Its welfare was the summum bonum of one’s life -- it was what the individual was to live for. The word “family” in China not merely mean, as in the West, the father and mother and their children: it was all inclusive and extended often to the whole clan. But, just as the family life was developed, so the community life was starved. The individual Chinese until recently and only in limited sense, always thought and acted in terms of the family. Therefore, the best things one formed in any city were family property: a family library; a family park; a family hall; a family art treasury, etc. It accounted in very substantial degree, for the lack of public spirit, and public service in Chinese community life. “I cannot think of any other agency as potential as our Rotary clubs to generate this spirit of public service,” he said.* (<cite data-cite="626961/N5ILEHTS"></cite>)
<!-- #endregion -->

In his address delivered at the Rotary Inter-City meeting held in Qingdao in 1935, the diplomat and political leader Wang Zhengting 王正廷 (1882-1961) advocated for the establishment of a modern public sphere, contrasting it with the traditional, family-centric vision of Chinese society. This excerpt, disseminated in both English and Chinese newspapers, prompts three overarching inquiries. Firstly, to what extent did Wang's idealistic vision align with prevailing perceptions and practices of social organization and public discourse? Secondly, how did the 1935 Rotary Club conference fit into the broader landscape of events and organizations that contributed to shaping the public sphere in modern China? Lastly, how did historical actors utilize the press to propagate their ideas and promote their actions to a wider audience?

<!-- #region citation-manager={"citations": {"": []}} -->
The question surrounding the emergence of a public sphere in China has been a longstanding subject of debate. Early studies in the 1990s primarily focused on theoretical considerations, particularly the applicability of Western concepts to the Chinese context  (<cite data-cite="626961/6M7LWV62"></cite>, <cite data-cite="626961/I283MNWA"></cite>, <cite data-cite="626961/4AQX8HJK"></cite>, <cite data-cite="626961/RRWSXTCT"></cite>, <cite data-cite="626961/KX6J2KTE"></cite>, reprinted in <cite data-cite="626961/U2J8FG4X"></cite>). Concurrently, social historians have examined manifestations of civil society, such as local elites in Zhejiang or civil protests in Beijing, to elucidate how the public sphere materialized through social practices (<cite data-cite="626961/96H7I4VF"></cite>, <cite data-cite="626961/J8VVKEE7"></cite>). Nevertheless, these investigations have been confined to specific local settings. While the twin concepts of the public sphere and civil society have diminished in prominence in Western scholarship, they continue to attract attention among Chinese scholars. A search for the term "公共领域" (*gonggong lingyu*), the most common equivalent of the English concept "public sphere," in the [Chinese National Knowledge Infrastructure (CNKI)](https://oversea.cnki.net/index/), a major bibliographic academic database, yields 505 journal articles published between 2004 and 2023. Among these, 108 articles pertain to the late Qing-Republican era, with 16 doctoral dissertations focusing on the same historical period. This extensive literature can be categorized into several key themes, including the development of the modern press during the late Qing-early Republican era; elite activism, and organizational innovation during the late Qing dynasty; the 1911 revolution, the founding of the Republic, and the emergence of citizenship; intellectual movements such as the New Culture and May Fourth movements in the 1910-1920s, and women's evolving social roles in the public realm. However, in most of these works, the term "public sphere" is employed metaphorically.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
Since the 2000s, the increased accessibility of newspaper collections has paved the way for novel avenues in studying the historical evolution of public opinion, prompting a renewed focus on the transnational dimension of the Chinese public sphere (<cite data-cite="626961/FY6ZQ7SB"></cite>, <cite data-cite="626961/2689WDL7"></cite>, <cite data-cite="626961/DLHJEUJA"></cite>). The transnational perspective gained prominence in the scholarship on modern China during the late 1990s and early 2000s, coinciding with the era of opening up and reform (1978-) and the post-revolutionary shift in Chinese historiography. According to China historian Arlif Dirlik, the term "transnational" encompasses two primary senses: (1) the traversing of national borders and (2) the convergence of different nationalities in specific "contact zones," with treaty ports and foreign settlements in post-opium-war China serving as exemplary instances (<cite data-cite="626961/GT2TR8Y6"></cite>). The ascent of the transnational perspective gave rise to an abundance of studies focused on Chinese "semi-colonial" modernity in treaty ports, notably Shanghai. While initially presented as an appealing alternative to both the Marxist concept of imperialism and Fairbank's "response to West" paradigm (Fairbank, 1954), the transnational paradigm has witnessed a decline in popularity over the past decade. Criticisms have emerged, characterizing it as a vague concept lacking robust conceptualization and  essentially “putting old wines into new bottles”. Furthermore, it has faced scrutiny for carrying an implicit ideological dimension that inadvertently downplayed or overlooked the unequal power relations engendered by global capitalism (<cite data-cite="626961/CDLF6DBW"></cite>).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
Methodologically, scholars investigating both the public sphere and the transnational dimension through the analysis of the press have commonly concentrated on individual publications. Their focus often narrows down to specific genres of articles, such as editorials or "free talk" (*Ziyou tan* 自由談) columns (See for instance: <cite data-cite="626961/GICNI827"></cite>, <cite data-cite="626961/ZV9JTLAI"></cite>, <cite data-cite="626961/HYY7TCKK"></cite>). Constrained by the limitations of human reading capacity, these scholars have typically relied on small samples of manually selected articles. However, this approach lacks the ability to contextualize findings and assess whether and to what extent the chosen texts or passages accurately represent broader trends. To alleviate the potential risk of reinforcing pre-existing assumptions or exaggerating individual perspectives, such as Wang Zhengting's binary conceptualization of Chinese society, a different methodological approach is warranted.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
This paper advances the ongoing debate by undertaking a joint empirical study of two institutions within the public sphere – a transnational organization, the Rotary Club, and the periodical press. The public sphere is conventionally defined as "the space in which state and society, as well as different segments of society, articulate their interests and opinions within culturally and historically defined rules of rationality and propriety" (<cite data-cite="626961/FY6ZQ7SB"></cite>, p.3). Building upon this definition, the public sphere is conceptualized as an alternative to armed conflicts, constituting "a key constituent of a social order whose members do not resort to violence in each instance when conflict occurs." Moreover, reconsiderations of Benedict Anderson’s theory regarding the modern press as a primary instrument for constructing national consciousness (<cite data-cite="626961/Z8NV2SVZ"></cite>) have led to the recognition that "the modern public sphere is not coterminous with the nation but is essentially transnational and international" (<cite data-cite="626961/FY6ZQ7SB"></cite>, p.3).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
The Rotary Club aligns seamlessly with these criteria. On one hand, it functions as a non-state organization with the purpose of socializing and legitimizing business and professional elites. On the other hand, it stands as a genuinely transnational organization, embodying the two senses defined by Dirlik. Established in Chicago in 1905, the Rotary Club expanded globally following World War I. By the eve of the Communist revolution in 1949, there were no fewer than thirty-three clubs in China, each hosting up to twenty different nationalities. Due to its foreign origins and multinational membership, the Rotary Club placed significant emphasis on international peace. Despite its professed apolitical stance, the organization was committed to fostering international goodwill among nations, particularly during the tumultuous interwar years (<cite data-cite="626961/4YPDTCZE"></cite>, p.233)
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
The second institution within the public sphere scrutinized in this research is the periodical press. Recognized as an invaluable source for historians of modern China, newspapers serve as a comprehensive record capturing the minutiae of everyday life while bridging the local and the global. Functioning as the earliest mass medium, the press played a crucial role as a platform through which various historical actors, including the Rotary Club, shaped their public image and sought to influence public opinion. Following the First Opium War (1839-1842), Shanghai emerged as the uncontested centre of the burgeoning modern press and publishing industry in China. The foreign settlements established by the Treaty of Nanjing (1842) acted as enclaves, fostering the development of a free press beyond the control of Chinese authorities (<cite data-cite="626961/FY6ZQ7SB"></cite>, p.4). The so-called "commercial" newspapers, primarily represented by commercially successful publications like *Shenbao* and *North-China Herald & Daily News*, experienced a significant boom during the Republican period (<cite data-cite="626961/RZEKCMV6"></cite>). Unlike intellectual pamphlets and political periodicals that thrived in the late Qing dynasty and during the New Culture and May Fourth (1919) movements of the 1910s-1920s, these commercial publications presented a broader spectrum of opinions.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
Fortunately, a considerable portion of the Shanghai press has been exceptionally well preserved to this day. Entire collections have been digitized, greatly facilitating scholars' access to these rich materials. This research focuses on the [ProQuest Chinese Historical Newspapers Collection](https://about.proquest.com/en/products-services/hnp_cnc/), recognized as the most extensive compilation of English-language periodicals produced in China before 1949, and the Chinese-language newspaper *Shenbao* (1872-1949). Although *Shenbao* does not encompass the entirety of the Chinese press, it stood as one of the two largest daily newspapers during the Republican era, boasting a circulation of 150,000 in the 1930s and maintaining the longest duration of publication (1872-1949). Significantly for this research, it is the sole full-text newspaper accessible for data mining, distinct from mere consultation through commercial platforms like [Airusheng](http://server.wenzibase.com) or [Green Apple (Qingpingguo shuju zhongxin)](https://www.egreenapple.com/english/channels/139.html) or academic databases like [CrossAsia](https://crossasia.org/). Both *Shenbao* and the ProQuest collection are accessible in the Modern China Textbase (MCTB), the reference textbase for modern China established by the [ENP-China](https://www.enpchina.eu/) (Elites, Networks, and Power in modern China) project. For this investigation, I relied on [HistText](https://bookdown.enpchina.eu/HistText_Book/), an application developed by ENP-China to harness large-scale historical digitized corpora in multiple languages, such as the MCTB (<cite data-cite="626961/25WN7ZZR"></cite>). Specifically, HistText enables the researcher to (1) construct a corpus tailored to a specific research question, (2) retrieve historical information such as named entities (names of persons, organizations, locations), and (3) transform the data to facilitate further analysis using various methods (statistical, textual, spatial, network, etc.). All these operations can be conducted autonomously within a single, integrated environment (R Studio).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
Within this framework, this paper pursues three primary objectives. Firstly, it seeks to complement prior research on the Rotary Club of Shanghai, primarily based on archival materials (<cite data-cite="626961/4YPDTCZE"></cite>). The previous study employed a prosopography approach to analyse Chinese membership and reveal internal tensions arising from the adoption of English as the primary language of communication among members. Building on this groundwork, this second paper delves into the club's public image, examining how the Rotary strategically utilized the periodical press to position itself as a public sphere institution dedicated to the "rational handling of conflicts." The key questions guiding this investigation are: (1) How did this non-state organization operate in practice on the local, national, and global scales? (2) Who were the key actors shaping its public image(s) and sphere(s) of action? (3) How did transnationalism manifest geographically in China during the Republican era? (4) What concepts were employed in the contemporary press, both Chinese and English, to characterize the transnational public?
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Secondly, by using the Rotary Club as a case study and the press as its primary source, this research aims to contribute more broadly to a re-examination of the debated question of the formation of a public sphere in Republican China. Drawing on new empirical data from the periodical press, the paper seeks to revitalize the elusive notions of "public sphere" and "transnationalism." My argument is twofold. First, I contend that these two concepts remain valuable frameworks for understanding the internal dynamics of non-state institutions like the Rotary Club and the Republican press. Second, I argue that the recent availability of full-text corpora of historical newspapers, coupled with the judicious use of computational methods, presents an opportunity to reconceptualize the public sphere and its "principles of rationality" as historically defined social constructs, shaped by evolving actors, events, and debates.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
I propose to utilize this case study as a proof of concept to develop a robust methodology for leveraging extensive collections of digitized newspapers in multiple languages. The aim is to inspire other historians working with similar materials or addressing comparable research questions. To address the complexities of investigating the transnational public as a historical subject and digitized historical newspapers as primary sources, this research integrates various methods, elaborated in detail within corresponding "hermeneutics" layers.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
This article is structured into four sections. The first section employs a bilingual topic modeling approach to analyse the operational modes of the Rotary Club in both the Chinese and English-language presses. Building upon this initial mapping, the second part integrates topic modeling, named entity recognition (NER), and network analysis to reconstruct the configuration of actors and topics influencing the public sphere throughout the Rotary Club's three decades of existence in China (1919-1949). The third part utilizes NER and Geographic Information Systems (GIS) to map the geographic imaginaries of Rotary members and associated actors. Finally, the fourth part scrutinizes the terminology used in both languages to conceptualize the public realm and its transnational dimensions.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
*Note: Due to the computational complexity of the various methods employed in this research, it was not feasible to integrate the code directly in the body of the paper. For the sake of legibility, the complete code is accessible on the dedicated [GitHub repository](https://github.com/carmand03/china-public-sphere) within the “script” folder. The paper only describes the most important steps and methodological choices that underpin the various methods in the corresponding hermeneutics layer. Interested readers can freely consult the detailed scripts either independently or in the course of their reading.*
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
## Part I. Modeling the Public Sphere: Topic Modeling of Rotary’s Operating Modes
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Topic modeling is a statistical method used to uncover hidden themes (topics) within large collections of unstructured texts. This approach relies on identifying co-occurrences of words in documents to reveal patterns and themes. Topic modeling proves especially fitting for this research endeavour focused on modeling the public sphere in the periodical press. Grounded in natural language, it is scalable and applicable to corpora of nearly any size. This methodology can be envisioned as a mixed-method approach that leverages the capabilities of unsupervised techniques to mitigate biases associated with manual reading and subjective selection. Simultaneously, it relies on close reading and contextual knowledge to interpret the topics automatically inferred. Through this hybrid approach, scholars can gradually narrow the divide between close and distant readings, quantitative and qualitative analyses, as well as theoretical and empirical studies.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
Historians have increasingly adopted topic modeling for various purposes, including refining corpus building, classifying documents, and mapping discourse dynamics and ideational changes (<cite data-cite="626961/JPQDI8X3"></cite>, <cite data-cite="626961/FUBAMMM3"></cite>, <cite data-cite="626961/VLTXFZ9R"></cite>, <cite data-cite="626961/IZHGPD6V"></cite>, <cite data-cite="626961/GT2TR8Y6"></cite>, <cite data-cite="626961/SW2G3JLE"></cite>, <cite data-cite="626961/TYNA7Q8G"></cite>). While initially applied predominantly in monolingual contexts, recent efforts have explored multilingual topic modeling (<cite data-cite="626961/4RLTTJBN"></cite>, <cite data-cite="626961/MJ4JJVIV"></cite>, <cite data-cite="626961/QHLTKGQB"></cite>, <cite data-cite="626961/ICISENGW"></cite>). In the realm of Chinese studies, topic modeling has found applications in both contemporary and classical Chinese texts, particularly in classical literature and historical records written in classical Chinese (<cite data-cite="626961/ZHQ5UL8D"></cite>, <cite data-cite="626961/DNUIWSYJ"></cite>). However, its application to modern Chinese newspapers has been limited due to the scarcity of digitized texts from that period.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
While historians have increasingly relied on topic modeling to navigate the expanding sea of digitized newspapers, few studies have explicitly tackled the challenge of article separation, although it is a crucial task for defining the appropriate unit of analysis. In most instances, the processing of digitized newspapers occurs at the page level, which lacks semantic coherence. Fortunately, in the ProQuest collection, layout analysis was conducted at a more granular level—individual articles. Nonetheless, specific sections like "Men and Events" or "Brevities" often encompass a variety of unrelated information ([figure 1](#anchor-figure-1)). The topics inferred from these heterogeneous articles may merely mirror their disordered contents, lacking immediate relevance to our specific research question. To our knowledge, only (<cite data-cite="626961/GT2TR8Y6"></cite>) and (<cite data-cite="626961/GWQTUMXN"></cite>) have addressed the critical issue of article separation in historical newspapers, though without presenting scalable solutions. (<cite data-cite="626961/IBT42XJB"></cite>) have also touched on the matter of determining text section sizes more generally.
<!-- #endregion -->

```R jdh={"object": {"source": ["Examples of problematic text units from *Shenbao* (top) and *China Weekly Review* (bottom). Segments of interest are highlighted. For the sake of saving space, only parts of the articles are reproduced here."], "type": "image"}} tags=["figure-1", "hermeneutics", "anchor-figure-1"]
library("IRdisplay")
display_jpg(file="./media/Fig1a.JPG")
display_jpg(file="./media/Fig1b.JPG")
```

<!-- #region tags=["hermeneutics"] -->
Focusing on the Rotary Club as a case study, this initial section addresses three significant methodological challenges: (1) the identification of topics related to this organization across multiple languages (English and Chinese in this paper); (2) the tracking of topical changes over time; and (3) the adaptation of topic modeling to the heterogeneity of newspaper contents, especially brevity-style articles comprising short, unrelated news pieces. This preliminary section unfolds in three steps. Firstly, it outlines the corpora and the methodology employed to prepare the text data and construct the topic models. Subsequently, the results of topic modeling are utilized to chart the Rotary Club's modes of operation and analyse how its local and global dimensions were presented in the press across languages. Lastly, an examination is conducted to trace the evolution of its operating modes during the tumultuous decades spanning from the end of World War I to the Communist revolution (1919-1949).
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
### Data and methodology
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The workflow follows three main steps: First, I created the text corpora. Second, I prepared the text data and built the topic models. Finally, I analysed and interpreted the topics. While this is a standard workflow in any topic modeling approach, this research introduces specific adaptations for building the bilingual corpora and for pre-processing the text data to overcome the problem of article separation described earlier.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics", "anchor-step-1-corpus-building"] -->
#### Step 1: Corpus building
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
In the first step, I created two separate corpora, one for each language. The Chinese-language corpus is based on the *Shenbao*, a leading newspaper published in Shanghai between 1872 and 1949. Despite low literacy rates among the Chinese population, the *Shenbao* reached 150,000 copies in the 1930s, making it one of the two most widely circulated newspapers in China (On the *Shenbao*, see <cite data-cite="626961/IE4K5VAI"></cite>, <cite data-cite="626961/IQFS98C6"></cite>, <cite data-cite="626961/5X6264E9"></cite>, see also [Christian Henriot's piece in this issue](https://journalofdigitalhistory.org/en/article/fwpktfFtn5jm)). Although it catered primarily to Shanghai intellectual, political, and business elites, its readership widened in the 1930s. The English-language corpus is based on the [ProQuest Chinese Newspapers Collection](https://about.proquest.com/en/products-services/hnp_cnc/), which includes a dozen of periodicals running from 1832 to 1953, with varying circulation, periodicity, and duration.  Despite the risk of overlap, I nonetheless chose to include all the periodicals included in the ProQuest collection to ensure the maximum coverage and to reduce the gap with the daily granularity of the *Shenbao*. Since the largest English periodicals were weekly publications, they were necessarily more selective than *Shenbao*, with the risk of missing some events that were reported in the *Shenbao*, but not in one or the other English periodicals. The most widely distributed foreign periodical was the *North-China Daily News*, peaking at 10,000 copies in the early 1930s, while its weekly edition, the *North-China Herald*, distributed almost 2,000 copies per week. They were read not only by foreign expatriates but also increasingly by foreign-educated Chinese elites. Although they were printed in Shanghai, both the *Shenbao* and the *North-China Herald* had a national, even international coverage, being circulated among overseas Chinese and foreign readers interested in Chinese affairs.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Since I am investigating a very specific organization with few possible homonyms and a low degree of ambiguity, I relied on simple keywords to build the corpora, namely “Rotary Club” in English and “扶輪社” (*Fulunshe*) in Chinese. I only excluded the quasi-homonym “國學扶輪社” (*Guoxue Fulunshe*), which referred to a publishing enterprise established in the early 20th century with no connection with the Rotary Club. Additionally, I restricted the query to the period posterior to 1919, when the first Rotary Club in China was established in Shanghai. For the English-language corpus, I used the metadata to filter out irrelevant or content-poor categories of articles, such as “Advertisement”, “Classified Advertisement”, “General Information”, and “Table of Contents, Front Matter”. The full code for building the corpora with the [HistText R library](https://bookdown.enpchina.eu/rpackage/HistTextRManual.html) can be found [here](https://bookdown.enpchina.eu/PublicSphere_stm/PublicSphere_Chinese.html#Corpus_building) (Chinese) and [here](https://bookdown.enpchina.eu/PublicSphere_stm/PublicSphere_English.html#Corpus_building) (English).
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Following this method, the query returned 467 documents spanning from 1922 to 1947 for the Chinese-language corpus (*Shenbao*) and 2387 documents published between 1919 and 1948 for the English-language corpus (ProQuest). The ProQuest corpus was predominantly composed of three large periodicals: *China Press* (a Sino-American joint venture) (1380, 58%), *North-China Herald* (British) (658, 28%), and to a lesser extent, *China Weekly Review* (American) (315, 13%). Obviously, the two corpora are not balanced. Not only is the English-language corpus larger than the Chinese one, but it also contains several periodicals. However, this is not an issue since the topics are inferred separately for each corpus based on their respective vocabulary. A major advantage of Latent Dirichlet Allocation (LDA)-based probabilistic models, as explained below, is their reliance on the relative frequencies of words in each topic and the relative proportions of topics in each corpus, enabling comparison across corpora of different sizes and structures.
<!-- #endregion -->

The two sets of plots below show the uneven distribution of documents over time in the two corpora ([figure 2](#anchor-figure-2)). The ProQuest corpus exhibits a clear peak in the 1930s, whereas the distribution was less regular in *Shenbao*. For both, we observe a significant gap during the Sino-Japanese War (1937-1945), particularly after 1941 when most periodicals ceased publication. In *Shenbao*, there was a gap in the data between November 1938 and October 1939, and then between January 10 and February 11, 1939, while for ProQuest, the gap occurs between 1941 and 1945. General statistics relating to the different collections, including the number of documents and tokens by year, are available on [GitLab, ENP-China group](https://gitlab.com/enpchina/ENP-Datasets-Stats).

```R jdh={"object": {"source": ["Distribution of documents mentioning the Rotary Club in *Shenbao* (top) and the ProQuest collection (bottom). The additional graphs serve to contextualize the results of the query. The second graphs (blue lines) show the percentage of the entire corpora that the query results represent."], "type": "image"}} tags=["figure-2", "hermeneutics", "anchor-figure-2"]
library("IRdisplay")
display_jpg(file="./media/Fig2a.JPG")
display_jpg(file="./media/Fig2c.JPG")

display_jpg(file="./media/Fig2b.JPG")
display_jpg(file="./media/Fig2d.JPG")
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 2: Text pre-processing
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
To tackle the issue of article separation, in the sense of extracting only the relevant news item from documents containing a mix of different news, this paper suggests a straightforward method based on concordance, or keyword in context (KWIC) ([figure 3](#anchor-figure-3)). This method unfolds in three steps. In the first step, I retrieved the key terms in their context using a concordance table a). The chosen key terms are the keywords employed in constructing the corpus: "Rotary Club" in English and “扶輪社” (*Fulunshe*) in Chinese (refer to [Step 1](#anchor-step-1-corpus-building)). In the second step, I merged the queried terms ("Matched") with the terms immediately preceding ("Before") and immediately following ("After") to reconstruct the sequence of words as a single string b).  Finally, in cases when the queried terms occurred multiple times in the same article, I reunited the article by merging its various instances in the same string c). The full code for retrieving concordance can be found [here](https://bookdown.enpchina.eu/PublicSphere_stm/PublicSphere_Chinese.html#Retrieve_concordance) (Chinese) and [here](https://bookdown.enpchina.eu/PublicSphere_stm/PublicSphere_English.html#Retrieve_concordance) (English). The main challenge with this method is to define the right context size for the concordance. For this purpose, I meticulously examined a sample of 50 documents of diverse sizes, covering a broad spectrum of genres and periods, to determine the most optimal context size for each language. Following this detailed analysis, I decided to establish an upper limit of 400 characters for Chinese and 100 for English. This decision reflects the smallest feasible context size in each language, aimed at minimizing the potential for overlap. While this solution may not be perfect, it demonstrated notable efficiency for a preliminary exploration of relatively large corpora comprising thousands of documents.
<!-- #endregion -->

```R jdh={"object": {"source": ["A simple three-step method for creating short text units centred on the queried terms using concordance or Key Word In Context (KWIC): (1) Retrieve KWIC (2) Reconstruct the sequence (3) Re-unite the document. The above example is taken from an article published in *Shenbao* on 14 April 1947, which contains three instances of the key terms."], "type": "image"}} tags=["figure-3", "hermeneutics", "anchor-figure-3"]
library("IRdisplay")
display_jpg(file="./media/Fig3.JPG")
```

<!-- #region tags=["hermeneutics"] -->
Next, I prepared the text data to make it processable by topic model algorithms. Standard pre-processing steps include tokenization, stemming, and lemmatization (optional), as well as various filtering options (stop words, punctuation, rare words). Tokenization involves segmenting the text into meaningful units, which, in this context, are essentially words. For the Chinese text, I used [jiebaR](https://github.com/qinwf/jiebaR/), one of the most popular tokenizers today. While primarily designed for tokenizing contemporary Chinese texts, it provided satisfactory results for texts published during the period under study (1919-1949). For the English text, I relied on the standard tokenizer included in the pre-processing function of the [stm R package](https://warin.ca/shiny/stm/#section-the-structural-topic-model), as described below. In the subsequent steps, I chose not to stem (i.e., reduce words to their root) or lemmatize words (reduce words to their common form) because, at this stage, I preferred to preserve all nuances conveyed in the original articles. Additionally, I provided a customized list of stop words, including the terms used for querying the corpus (“扶輪社”, “Rotary”, “club”) and common terms in this context, such as “中國”, “上海”, “China”, and “Shanghai”. Furthermore, I removed words containing fewer than two characters and occurring in fewer than two documents in Chinese, and those containing fewer than four characters and occurring in fewer than five documents in English. With these parameters, five documents were removed from the Chinese corpus. The resulting corpora eventually contain 2378 terms in English and 921 in Chinese, representing their respective vocabularies.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 3: Model building
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Various topic modeling algorithms have been implemented so far. For this research, I opted for a Latent Dirichlet Allocation (LDA) algorithm, which is one of the most popular methods today. LDA is a probabilistic model that treats topics as mixtures of words and documents as mixtures of topics. This implies that words can belong to different topics, while topics can be represented in multiple documents with varying proportions. More specifically, I relied on structural topic modeling (STM) to incorporate metadata such as the date of publication in order to investigate the effect of time on topical prevalence. From a technical perspective, I chose to use the [stm R package](https://warin.ca/shiny/stm/#section-the-structural-topic-model) which includes several built-in functions designed to facilitate the exploration of topics, including various visualizations and statistical outputs (<cite data-cite="626961/WA2GBZDB"></cite>). The full code for building the topic models in [Chinese](https://bookdown.enpchina.eu/PublicSphere_stm/PublicSphere_Chinese.html#Model_building) and [English](https://bookdown.enpchina.eu/PublicSphere_stm/PublicSphere_English.html#Model_building) is available in the GitHub repository.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
Choosing the right number of topics *k* remains a highly debated question. There is no definite answer. Most topic modeling tools, including the *stm* package, generally provide a set of metrics such as held-out likelihood, residual analysis, average exclusivity and semantic coherence, to help the researcher to determine the optimal number of topics for a given corpus. According to the creators of the *stm* package, the optimal number of topics for corpora that comprise between a few hundred to a few thousand documents, should range from 5 to 50 topics (<cite data-cite="626961/CTH9XCRS"></cite>).  Ultimately, however, only the researcher’s interpretational needs can determine the most appropriate number of topics for a given specific research. Rather than concentrating on a singular, definitive model, I decided to build three models with 5, 10, and 20 topics for each corpus. Multi-model approaches have been effectively employed in prior studies (<cite data-cite="626961/AG6AGH4A"></cite>, <cite data-cite="626961/7ANYDUV2"></cite>). This approach allows scholars to navigate between various levels of granularity and choose, in each model, the topics most pertinent to their research question. It is particularly well-suited for this case involving corpora of varying sizes and structures.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The results of topic modeling are usually presented in the forms of lists of words and probabilities. Each topic is defined by a series of words which most frequently co-occur together. Topics are also associated with their global proportion in the entire corpus and their relative proportion per document. The series of plots below shows the most frequent words for each topic and the relative proportion of the topics for each model ([figure 4](#anchor-figure-4), [figure 5](#anchor-figure-5)).
<!-- #endregion -->

```R jdh={"object": {"source": ["Summary of topics for each model in the Chinese corpus. Each plot shows the most frequent words for each topic and the relative proportion of the topics for each model."], "type": "image"}} tags=["figure-4", "hermeneutics", "anchor-figure-4"]
library("IRdisplay")
display_jpg(file="./media/Fig4a.JPG")
display_jpg(file="./media/Fig4b.JPG")
display_jpg(file="./media/Fig4c.JPG")
```

```R jdh={"object": {"source": ["Summary of topics for each model in the English corpus. Each plot shows the most frequent words for each topic and the relative proportion of the topics for each model."], "type": "image"}} tags=["figure-5", "hermeneutics", "anchor-figure-5"]
library("IRdisplay")
display_jpg(file="./media/Fig5a.JPG")
display_jpg(file="./media/Fig5b.JPG")
display_jpg(file="./media/Fig5c.JPG")
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
Based on the list of words, I labelled the topics in the most meaningful way as possible ([figure 6](#anchor-figure-6), [figure 7](#anchor-figure-7)). In cases where topics seemed unclear, I did not solely rely on the list of words; instead, I closely examined a sample of highly representative texts for each topic to better understand how the topics translated into concrete words and sentences. Additionally, I drew on my previous knowledge of the club and the broader historical context to enhance my final interpretation of the topics.
<!-- #endregion -->

```R jdh={"object": {"source": ["Topic labels for each model in the Chinese corpus."], "type": "image"}} tags=["figure-6", "hermeneutics", "anchor-figure-6"]
library("IRdisplay")
display_jpg(file="./media/Fig6a.JPG")
display_jpg(file="./media/Fig6b.JPG")
display_jpg(file="./media/Fig6c.JPG")
```

```R jdh={"object": {"source": ["Topic labels for each model in the English corpus."], "type": "image"}} tags=["figure-7", "hermeneutics", "anchor-figure-7"]
library("IRdisplay")
display_jpg(file="./media/Fig7a.JPG")
display_jpg(file="./media/Fig7b.JPG")
display_jpg(file="./media/Fig7c.JPG")
```

<!-- #region tags=["hermeneutics"] -->
Tables 1 to 6 in the ([Appendix](#anchor-appendix)) provide a summary of the topics for each model, including their label, the 10 most frequent words defining each topic, and their various attributes (topical group, dimension, proportion, and trend over time). Tables 7 and 8 show the topics aligned across models. Tables 9, 10, and 11 present the topics aligned across languages.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
### The *modus operandi* of the public sphere
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
In the next step, I grouped the labelled topics into four broad categories ([figure 8](#anchor-figure-8)). These four meta-topics reflect the four main domains of activity of the Rotary Club, and by extension, to the four *modus operandi* of the public sphere.
<!-- #endregion -->

```R jdh={"object": {"source": ["Distribution of topical categories. PQ = ProQuest, SB = *Shenbao*. 5T = 5-topic model, 10T = 10-topic model, 20T = 20-topic model."], "type": "image"}} tags=["figure-8", "hermeneutics", "anchor-figure-8"]
library("IRdisplay")
display_jpg(file="./media/Fig8.JPG")
```

<!-- #region tags=["narrative", "hermeneutics"] -->
**Meeting, socializing, entertaining (blue)**. This category refers to the weekly meetings (tiffins) held every Thursday by the Shanghai Rotary Club (lunch, tiffin), as well as special events (dinner dance, concert, garden party) and sports games, such as the Rotary Tennis Cup organized every year in the early 1930s. In the *Shenbao* corpus, this group includes topics 4 and 5 in the 5-topic model, topics 1, 10, 8, 5, and 4 in the 10-topic model, and topics 4, 8, 16, 3, 5, and 1 in the 20-topic model. In the ProQuest corpus, this group includes topics 5 and 1 in the 5-topic model, topics 7, 5, and 8 in the 10-topic model, and topics 8, 17, 5, 11, and 9 in the 20-topic model.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
**Sponsorship and community service (grey)** refers to various philanthropic projects aimed at both elite (students, boy scouts) and non-elite populations (poor Russian emigres, poor children, the blind, war refugees). In the *Shenbao*, this group includes topic 1 in the 5-topic model, topics 9 and 6 in the 10-topic model, topics 17, 9, 10, 12, and 6 in the 20-topic model. In the English-language press, this group includes topics 4 and 2 in the 5-topic model, topics 2 and 6 in the 10-topic model, and topics 10, 15, 7, and 6 in the 20-topic model.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
**Organization (yellow)** includes topics dealing with elections of local and district officers, Rotary International delegates, national and international conferences, relations with Rotary International, exchanges between Rotary clubs in China and other countries. In *Shenbao*, this group is specifically represented by topic 2 (Rotary International) in the 5-topic model, by topic 7 (district elections) in the 10-topic model and becomes more prominent in the 20-topic model (topics 18, 2, 15, 20, 13, and 7). In ProQuest, organizational issues emerge as a topic in the 10-topic model (topic 10 on non-Shanghai clubs) and gain importance in the 20-topic model (topics 1, 12, 13, and 20).
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
**Forum (orange)** refers to lectures given during tiffin-meetings and speeches delivered by official guests during special events. The discussions covered a variety of topics, including economic development, social welfare, health, technology, Chinese arts and cultural exchanges. In *Shenbao*, this topical group emerges only in the 10-topic model (topics 2 and 3) and remains under-represented in the 20-topic model (topics 14 and 19). It is more prevalent in the English-language press, represented by topic 3 in the 5-topic model, topics 10, 4 (social work), and 9 (Sino-Japanese relations) in the 10-topic model, and by topics 4 (social work), 3 (American and East Asia), and several opinion articles (topics 14, 10, 19) in the 20-topic model.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
**Other (pale blue)**. The remaining topics are classified as ambiguous or irrelevant. They often present a low semantic coherence, which reflects the polysemous nature of the words they include. Topic 11 in the 20-topic model of the *Shenbao* provides an example of a non-topic made up of three distinct issues: (1) Sino-American relations (speech of the Chinese general consul before the New York Rotary Club regarding Sino-American friendship, Rotary International scholarship for students in the United States), (2) a series of advertisements for a toy collection campaign, and (3) various meetings. The connection between (2) and (3) is made through the “Metropole Hotel” (都城飯店 *Ducheng fandian*) which is used both as a place of meeting and a place for collecting toys, whereas the connection between (1) and (3) is made through the word “speech” (演說 *yanshui*). In the English corpus, topics 14, 10, and 19 in the 20-topic model contain unrelated articles that share very general words, such as “life”, “business”, “said”, and “address”. In an improved version of the model, these generic words should be removed to increase the relevance of topics.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
As these examples suggest, invalid topics tend to become more frequent as we increase the number of topics in the model. This can be measured by plotting topic coherence against exclusivity, as shown on the plot ([figure 9](#anchor-figure-9)). The higher the number of topics, the lower the coherence, and the higher the exclusivity. Both coherence and exclusiveness are important for creating meaningful and useful topics in topic modeling. Topic coherence measures how semantically related words within a topic are. A coherent topic is one where the words that define the topic are contextually similar and make sense together. High coherence indicates that the words within a topic are more likely to represent a meaningful and interpretable theme or concept. It helps in understanding and labelling topics more effectively. Topic exclusiveness refers to the extent to which words in one topic are distinct and do not overlap with words in other topics. In other words, each topic should be unique and capture a specific aspect of the corpus. Exclusiveness is important to avoid ambiguity and ensure that topics are well-separated. In this paper, topic coherence and exclusiveness have been calculated using the specific functions available in the stm package — *stm::semanticCoherence()* and *stm::exclusivity()*. For further details, please refer to the GitHub repository and the [stm package documentation](https://cran.r-project.org/web/packages/stm/index.html).
<!-- #endregion -->

```R jdh={"object": {"source": ["Plotting semantic coherence against exclusivity for the three models built from *Shenbao* (top) and ProQuest (bottom). The higher the number of topics, the lower the coherence, and the higher the exclusivity."], "type": "image"}} tags=["figure-9", "hermeneutics", "anchor-figure-9"]
library("IRdisplay")
display_jpg(file="./media/Fig9a.JPG")
display_jpg(file="./media/Fig9b.JPG")
```

<!-- #region tags=["narrative", "hermeneutics"] -->
Meeting-related topics prevail in both corpora (40 to 60%), meaning that socializing and entertaining were the primary functions of the club. Local meetings were particularly prominent in the *Shenbao*, which essentially reflects the daily periodicity of the newspaper. The *Shenbao* contains a fairly large number of repeated announcements of upcoming meetings, whereas the English-language weekly press featured less frequent but more substantial reports of past meetings.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
Community service was the second most important activity of the club (10 to 30%). The two corpora shared a similar concern for children, reflected in the toy collection campaigns that the Rotary organized every year for Christmas (SB20T06), and the fundraising campaigns aimed at building a children hospital in Zhabei (north of the International Settlement) (SB20T12). In fact, children-oriented philanthropy represented the most prevalent and resilient topic in this category. The 20-topic models also shared a growing concern for helping poor Russian emigres in Shanghai (SB20T10, PQ20T15). Boy scouts featured more prominently in the English-language press (PQ5T04, PQ10T06, PQ20T06), whereas the *Shenbao* was more concerned with the construction of a “beggar camp” for refugees during the Sino-Japanese war (SB10T09, SB20T17). These divergences reflect both the national profiles of the individuals who were involved in the various charity projects, as well as the uneven impact of the Sino-Japanese war (1937-1945) on the Chinese and the English press. On the one hand, the Boy Scout movement in Shanghai was essentially supported by the British Rotarian Francis Charles Millington. On the other hand, the English-language press was more seriously affected by the war than the *Shenbao*.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["narrative", "hermeneutics"] -->
The greater prevalence of organizational topics in the *Shenbao* (25% compared to 5% in the ProQuest corpus) reflects the general growth of Chinese members and the increasing autonomy of Chinese clubs in the global organization (<cite data-cite="626961/4YPDTCZE"></cite>).  While the English press focused on local elections prior to the Sino-Japanese war (PQ10T01, PQ20T20), the Chinese press seemed more concerned with district elections and postwar reorganization (SB10T07, SB20T07). Both corpora reported on other Rotary clubs in China (PQ10T03), including Tianjin (PQ20T18, SB20T15), Nanjing (PQ20T13), after the Nationalists had established their capital in the city in 1927, and Hangzhou, where the first Chinese-speaking club was established in 1931 (SB20T18) (<cite data-cite="626961/4YPDTCZE"></cite>, p.254).  While international conventions were systematically documented in the two corpora (SB5T02 , SB10T02, SB20T02, PQ20T01), *Shenbao* was more likely to report on other Rotary clubs outside Shanghai (SB20T13, SB20T20).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["narrative", "hermeneutics"] -->
Finally, the presence of forum-related topics (5 to 20%) in the two corpora illustrates a core characteristic of the public sphere as an alternative to armed conflicts (<cite data-cite="626961/FY6ZQ7SB"></cite>, p.5). It is remarkable that in both languages, every topic is deprived of any words denoting conflict or violence. Instead, the words that dominate the six topic models all emphasize dialogue and discussion as the primary means of communication among Rotarians. These words also express the self-image that the Rotary aimed to present to the world. For instance, if we focus on the 10-topic model, topic 2 is defined by the words *yanshuo* 演說 (speech), *daibiao* 代表 (delegate or representative), *qinshan* 親善 (goodwill), and *jingshen* 精神 (spirit) in Chinese. These words serve to define other topics as well, and in fact they occur frequently across the entire corpus. In the English-language press, the words “said”, “address”, “speech”, and “talk” are highly frequent in topic 10 as well as in other topics. These topics epitomize the self-claimed apolitical nature of the Rotary Club and its commitment to international peace and goodwill. Potentially conflictual issues were always discussed on a rational basis during meetings and special events, which offered a platform for guest speakers, including government officials, to defend their opinions and political programs in their keynote speeches. The Rotarians’ mode of communication and ways of managing conflicts contrasted sharply with the "war of resistance" advocated by other Chinese organizations during the same period.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
The “forum” category nonetheless presents significant differences between the two corpora in terms of topic prevalence and topical contents. Forum-related topics were more prevalent in English periodicals than they were in the *Shenbao*. This again essentially reflects the weekly periodicity of English-language press, which allowed for lengthy and more detailed accounts of lectures and discussions, whereas the Chinese daily was more likely to publish brief accounts and announcements of lectures. Furthermore, the English press tended to focus on social/economic issues (PQ10T04 and PQ20T04) and international relations, especially the American presence in East Asia (PQ20T03). The two corpora shared a growing concern for Sino-Japanese relations after the Japanese invasion of Manchuria in September 1931. This critical topic, however, was not as prominent as expected and made only brief appearances in both corpora (PQ10T09, SB20T19).
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["narrative"] -->
### Negotiating between the local and the global
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["narrative", "hermeneutics"] -->
To investigate the transnational nature of the public sphere, I further classified the topics into local/non-local categories. In this research, the term 'local' reflects the Shanghai point of view. Since the periodicals under study were published in Shanghai and catered primarily to a Shanghai-based audience, "local" refers to the perspective of Shanghai newspaper readers. In both languages, the local perspective can be empirically identified through terms referring to local places (street names, buildings, or hotels where the Rotary Club held its meetings), local time (day, date, exact time of meetings), local institutions (local companies or branches of external companies, municipal administration, civic associations, or local business organizations), and local positions (president, manager, director, board member). The local perspective, however, is not defined by individuals such as Rotary members or guests, who were mobile both geographically and professionally, and whose mindset and influence extended far beyond their daily routines and local spheres of action.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
How did the transnational dimension of the Rotary Club perspire through its four operating spheres? First, as a transnational organization, the Rotary Club had local branches with a large degree of autonomy from its centre in Chicago, which is reflected in several topics dealing with local elections, district elections and national conventions (SB10T07, PQ10T01, SB20T07, PQ20T01, PQ20T12, PQ20T20). Second, topics related to community service reveal the implications of global conflicts on local philanthropy, as in the case of war refugees (SB10T09, SB20T17). Topics related to lectures and speeches (forum) often dealt with global issues, such as international relations, political economy, and cultural exchanges across national boundaries (SB10T02, PQ10T09, PQ10T10, SB20T19, PQ20T03). Finally, topics related to meetings and socializing arenas reveal that Chinese Rotary clubs received many visitors from abroad, including Rotary International delegates and representatives of other clubs in Asia and Western countries (SB20T01, PQ20T05). From the perspective of the local press, Shanghai emerged as the new regional and global centre in East Asia. Circulations went both ways. Not only did foreign visitors come to China, but Chinese Rotarians as well frequently visited other clubs in foreign countries.
<!-- #endregion -->

<!-- #region tags=["narrative", "hermeneutics"] -->
The distinction between local and non-local topics, however, is not always straightforward. In LDA-based models, topics are mixtures of words which can be both localized and globalized. This can be best illustrated by focusing on the words that define each topic. The following examples are taken from the 10-topic model ([figure 10](#anchor-figure-10)).
<!-- #endregion -->

```R jdh={"object": {"source": ["The most frequent words defining the 10-topic models in *Shenbao* (top) and ProQuest (bottom)."], "type": "image"}} tags=["figure-10", "hermeneutics", "anchor-figure-10"]
library("IRdisplay")
display_jpg(file="./media/Fig10a.JPG")
display_jpg(file="./media/Fig10b.JPG")
```

<!-- #region tags=["narrative", "hermeneutics"] -->
Topics 1 and 3 in the Chinese corpus provide examples of mixed topics including both local and non-local terms (see [figure 10](#anchor-figure-10) and [figure 11](#anchor-figure-11)). Topic 1 includes words that refer to the United States (美国) (American guests) as well as tiffin meetings (聚餐會) in local hotels (都成飯店 Metropole Hotel) at local time (昨日 yesterday, 星期四 Thursday, 十二時 noon). Topic 3 is defined by terms that refer to other countries (各国) as well as local time (昨日  yesterday), local place (本埠 this port), local institutions (該社 this club) and local positions (社員 club member, 主席 chairman). Topics 6, 8, 9, and 10 are more clearly local (兒童, 苦兒, 醫院: local children hospital, 影片: local movie projection, 下午 : this afternoon, 二時 : two o’clock, 四川, 馬路 : street names), whereas topics 2, 4, 5, 7 refer to more distant settings and events (國際 international, 萬國 universal, 世界 world, 代表 delegate, 親善 goodwill, 日本 Japan, 天津 Tianjin, 本月 this month, 區域 district).
<!-- #endregion -->

```R jdh={"object": {"source": ["The most representative documents for topics 1 and 3 in the Chinese-language corpus (10-topic model)."], "type": "image"}} tags=["figure-11", "hermeneutics", "anchor-figure-11"]
library("IRdisplay")
display_jpg(file="./media/Fig11.JPG")
```

<!-- #region tags=["narrative", "hermeneutics"] -->
In the English corpus, mixed topics include topics 1, 5, and 10 ([see figure 12](#anchor-figure-12)). Topic 1 deals with the elections of local club officers (board, elected, president, secretary, Shanghai) with an international stature, such as Kuang Fuzhuo 鄺富灼 (1869-1938), an American-educated Chinese who served as president of the Shanghai Club as well as delegate of Rotary International, district governor and leader of the Young Men’s Christian Association (YMCA). Topic 5 deals with American residents and visitors in Shanghai, exemplifying the transnational flows of people coming and going every day through the treaty port. Topic 10 refers to speeches that addressed global issues during a local meeting in Shanghai. More clearly global topics includes topics 3 & 9 (about Japan), whereas topics 2, 4, 6, 7, and 8 are more clearly locally grounded.
<!-- #endregion -->

```R jdh={"object": {"source": ["The most representative documents for topics 1, 5, and 10 in the English-language corpus (10-topic model)."], "type": "image"}} tags=["figure-12", "hermeneutics", "anchor-figure-12"]
library("IRdisplay")
display_jpg(file="./media/Fig12.JPG")
```

<!-- #region citation-manager={"citations": {"": []}} tags=["narrative", "hermeneutics"] -->
The fact that topics are often mixtures of local/non-local words complicates the categorizations designed in the beginning of this section. Furthermore, when taken out of their context, some words appear ambiguous. Deciding on their local/non-local dimensions usually requires additional, contextual knowledge. For example, as shown on [figure 10](#anchor-figure-10), the words “都城” (*ducheng*) in topic 1 and “Metropole” in topic 7 did not refer to some global metropolis but to the name of a local hotel in Shanghai (都城 飯店 *Ducheng fandian*), which the Rotary Club used for its weekly meetings in the 1930s. Alternative text analysis tools such as bigrams and collocations can be used in combination with topic modeling to help disambiguate such words. Ultimately, disambiguation requires a close reading of sample texts, usually the top first documents with the highest topic prevalence, to better understand how topics translate into concrete words and sentences, and to eventually validate the actual content of topics (<cite data-cite="626961/ADRQ6K6S"></cite>).
<!-- #endregion -->

### The public sphere over time


How did the public sphere evolve over time? Did the war reshape the four domains of the public sphere? Did the Shanghai press and the Rotary Club become more globally minded in times of international crisis? For this temporal analysis, I continued to rely on the 10-topic model, which offers the best compromise. The 5-topic models contain topics that are too broad and difficult to interpret, whereas the 20-topic models include overlapping topics, non-topics, and topics that are exclusive to single documents. Eventually, the 10-topic model is more balanced and lends itself to more meaningful interpretation.


*Note: In the following, the notions of topic evolution and stability refer to how the distribution of topics changed or persisted over time, depending on the social-political context. The focus is at the corpus level, not the topic level. It's important to distinguish topic stability in this research from the technical notion of topic stability, which refers to the amount of change in the topic content over multiple runs of the algorithm on the same corpus. Similarly, topic evolution should not be understood in the technical sense of evolving vocabulary, changing social meanings of words, or changes in words' usage habits.*


In the two corpora, local meetings tended to decline over time, whereas discussions and local philanthropy driven by international conflicts tended to increase during the same period. In  *Shenbao*, three topics in particular experienced a significant decline. These topics refer to special events and social gatherings aimed at entertaining members (topic 4) and guest speakers (topic 3). Topic 5 also includes sports games, especially the Rotary Tennis Cup which was exclusive to the 1930s decade. In the ProQuest corpus, weekly meetings, and special events (topics 6, 7, 8) also declined during the war and the post-war period. Either meetings ceased during the war, or they were no longer systematically reported in the press. On the opposite, topics 2 and 7 experienced a notable increase in the Chinese corpus. Topic 2 reveals that transnational flows of people did not stop during the war. From this topic, we learn that Rotary clubs in China continued to host visitors from abroad, including Rotary International delegates and fellow Rotarians from other countries. Topic 7 relates to the post-war reorganization and the elections of regional delegates at the district level. In the ProQuest corpus, rising topics essentially relate to children's welfare during the war (topic 2), Japan (topic 9), and various lectures about global issues ([figure 13](#anchor-figure-13)).

```R jdh={"object": {"source": ["Topic proportions over time (1919-1949) for the 10-topic model in *Shenbao* (top) and ProQuest (bottom). Topic proportions are aggregated by year."], "type": "image"}} tags=["figure-13", "anchor-figure-13"]
library("IRdisplay")
display_jpg(file="./media/Fig13a.JPG")
display_jpg(file="./media/Fig13b.JPG")
```

The remaining topics seem less stable. Topics 1, 6, 8, 9, and 10 in the Chinese corpus are examples of such unstable topics. Most refer to tiffin meetings (announcements or reports), which constitute a regular feature of the Rotary Club and can be defined as a “background topic” for the Rotary Club. Topics dealing with children peaked during the war and vanished afterwards. Topics dealing with the beggar camp and the refugee problem also peaked during the war. Their early appearances are misleading, however, resulting from polysemous terms used to define different topics (such as *xiwang* 希望 “hope”).


In the English corpus, temporally unstable topics include topics 1, 3, 4 (social work), and 5. These topics consist of less consistent themes addressing different issues defined through similar terms. Topic 1 relates to various elections and organizational issues. Topic 3 deals with Rotary clubs outside of Shanghai, appearing mostly in the mid- and late 1930s. Topic 4 addresses a range of issues related to social work and workers, including labour strikes in the 1920s, the development of Greater Shanghai and the new Chinese municipality in the 1930s, as well as epidemics and public health administration during the war. Finally, topic 5 focuses on the American community, Sino-American relations, and the movement of American visitors in China. This topic emerges as another background topic for several reasons. With the growing influence of the United States in the Pacific region after WWI, an increasing number of American businessmen and officials came to work in China in the 1920s-1940s. After the Sino-Japanese war, the United States reinforced their influence in the region in the context of the Chinese civil war and the Cold War on the global stage. Additionally, this topic reflects the permanence of “People and Events” sections in English-language periodicals, a particular genre of brief news articles focusing on people’s life events. Eventually, from the 1930s onwards, it becomes increasingly difficult to disentangle local and global topics due to China’s increasing participation in the globalized world, especially during the Sino-Japanese war (1937-1945).


## Part II. Populating the Public Sphere: Configurations of Actors


This section builds upon the outcomes of the preceding topic modeling to delve deeper into the contents and individuals involved in the Rotary Club and its associated public sphere. The primary questions guiding this exploration include: (1) What were the principal themes, issues, and debates that captured the attention of Rotarians and related actors? (2) Who played a role in shaping these debates? Who were the key actors, either individually or collectively, that defined the transnational public sphere(s)? (3) How did the identified topics and actors differ across periodicals in various languages? What insights do these differences offer regarding newspaper editors' access to information and their assessment of readers' concerns? (4) How did the topics and actors evolve over time, influenced by internal or external factors? How were they shaped by Rotary Club's internal history, external events, or developments in the newspaper industry and journalistic profession during the Republican era?


The following hermeneutics layers outline the five-step methodology employed for refining corpora and reconstructing the networks of topics and actors over time. Subsequent narrative layers present key findings for each time period. The complete code is accessible in the "script" folder on the GitHub repository.

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
### Methodology
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 1: Filtering topics
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
To conduct a more in-depth exploration of the contents and actors within the public sphere, I opted to concentrate on topics related to lectures and speeches, as these provide substantial content for debates and diverse perspectives. Specifically, I focused on topic 3 in the 5-topic model within the English corpus and topics 2, 3, and 10 in the 10-topic model within *Shenbao* (refer to Tables in the Appendix for details). Within each topic, I retained articles that exhibited a minimum proportion of the selected topics. The determination of this minimal threshold requires clarification. While previous studies recommended a minimum of 25% (<cite data-cite="626961/IBT42XJB"></cite>), this research adopts a more flexible approach based on the document topic distribution in each corpus and model, as illustrated in the histograms ([figure 14](#anchor-figure-14)). Given the relatively small size of the corpora (hundreds of articles), this method aims to avoid excluding too many documents. Following this method, I selected all documents containing at least 0.11% of topic 3 in the English corpus 10-topic model. In the Chinese corpus, I retained 0.02% of topic 2, 0.01% of topic 3, and 0.02% of topic 10.
<!-- #endregion -->

```R jdh={"object": {"source": ["Histograms illustrating the document-topic distribution in the 5-topic model applied to the *Shenbao* corpus (above) and the 10-topic model of the English corpus (below)."], "type": "image"}} tags=["figure-14", "anchor-figure-14"]
library("IRdisplay")
display_jpg(file="./media/Fig14a.JPG")
display_jpg(file="./media/Fig14b.JPG")
```

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 2: Refining text units
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
To comprehensively analyse the debates and actors present in the press, it is essential to consider entire news items as units of analysis, unlike the selected text segments used in the previous section to model the operating modes of the Rotary Club. This necessitates several additional pre-processing steps, which vary depending on the language. In the English corpus, I filtered the texts by category to retain only "feature articles" and remove brevities and other categories containing brief announcements with little substantial content. After filtering, the new English corpus contained 954 documents. In *Shenbao*, it was not possible to apply this method since no classification was available. Therefore, I reviewed the documents one by one to extract the relevant passages from each document and then computed the length of each passage to retain only substantial news items. Based on the set of manually re-segmented articles, I filtered out the shortest documents that did not contain any substantial information, such as brief announcements of meetings. After a close examination of the shortest texts, I set the threshold to 45 characters and removed all documents (166) containing less than 45 characters. After filtering, the final Chinese corpus contained 345 documents.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 3: Time-based topic modeling
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics", "narrative"] -->
To explore the evolution of topics over time, I divided the two datasets (English and Chinese) into three time slices, corresponding to three key periods in the history of the Rotary Club (<cite data-cite="626961/4YPDTCZE"></cite>):
**(1) The first phase (1919-1929)** corresponds to the first decade in the club's history, marked by post-WWI debates regarding peace, international relations, and social reforms.
**(2) The second period (1930-1937)** is characterized by the growth of Chinese membership and leadership, with new concerns for social reform and the global economic depression.
**(3) The final phase (1938-1949)** is shaped by concerns with war relief and post-war reconstruction.
<!-- #endregion -->

This division resulted in six sub-corpora, three for each language ([table 12](#anchor-table-12)). Based on the refined, high-quality corpora derived from the results of the previous topic modeling, I conducted a second round of topic modeling (using LDA as well) on each time-based corpus. The objective was to identify the key issues defining each time period and each language. Given the relatively small size of the six time-based corpora, I opted to retain 5 topics for each dataset, which I found sufficient to capture the range of issues at stake. The results of this time-based topic modeling are summarized in the tables below ([table 13](#anchor-table-13), [table 18](#anchor-table-18), [table 23](#anchor-table-23)). The detailed code for building models is available in the "script" folder on the GitHub repository.

<!-- #region jdh={"object": {"source": ["Number of documents by subcorpus."], "type": "table"}} tags=["hermeneutics", "table-12", "anchor-table-12"] -->

| **Period**    | **Chinese** | **English** |
|---------------|-------------|-------------|
| **1919-1929** | 62          | 184         |
| **1930-1937** | 141         | 687         |
| **1938-1949** | 142         | 83          |
| **Total**     | 345         | 954         |
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 4: Retrieving actors
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
To reconstruct the configurations of actors that shaped the public sphere and its ideological contents (debates and key issues), I employed **Named Entity Recognition (NER)**, a well-established method in natural language processing that enables the identification of names of persons, organizations, locations, and other entities in text corpora. In this specific research, NER was utilized to extract the names of persons, organizations, locations, and geopolitical entities (GPE) in the two language-based corpora under study.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} tags=["hermeneutics"] -->
I specifically utilized models developed by Baptiste Blouin, a computer scientist in the ENP-China project, for extracting historical entities in digitized texts in Chinese and English. These refined models, trained on appropriate historical data, offer several crucial advantages: (1) they are robust to noisy Optical Character Recognition (OCR) and missing punctuation, notably in the ProQuest collection of English-language newspapers; (2) they can identify the names of persons in Chinese, taking into account variants, co-references, and embedded titles (such as 君jun). More information on these models can be found in the [HistText manual](https://bookdown.enpchina.eu/HistText_Book/named-entity-recognition-ner.html) and Blouin’s related papers (<cite data-cite="626961/THBIYZ7E"></cite>, <cite data-cite="626961/U433KHD5"></cite>, <cite data-cite="626961/XN9I57AE"></cite>). The workflow used for extracting and cleaning the entities in this research is described in detail in the "script" folder in the GitHub repository.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
#### Step 5: Building Networks
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
In the subsequent step, [Cytoscape](https://cytoscape.org/) (a popular network analysis software) was employed to construct and visualize the two-mode networks linking the entities (persons and organizations) and the documents in which they are mentioned. For the sake of legibility, interested readers can explore interactive versions of these networks on [NDex](https://www.ndexbio.org/#/networkset/6515e8eb-b92f-11ee-8a13-005056ae23aa?accesskey=1a3017d172630cbbf57b719844c94fbfd7b59cab8ed12b1bdfb10bc0d6a53a78). Network visualizations proved extremely helpful for exploring the connections between actors, documents, and topics, using topic proportions per document as node (document) attributes. Since a given document can be composed of different topics in varying proportions, I applied **Principal Component Analysis (PCA)** to the topic-document proportions and hierarchical clustering (HCPC) to cluster the documents according to their topical composition. PCA is a dimensionality reduction technique commonly used in data analysis and machine learning. The primary goal of PCA is to transform high-dimensional data into a new coordinate system, called principal components, where the data's variance is maximized along the axes. This is achieved by identifying the directions (principal components) along which the data varies the most. For further details on the methodology used for PCA and HCPC, additional information can be found on GitHub in the script folder.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Furthermore, network metrics were utilized to identify the most central persons in the networks, representing key actors shaping the Rotary public sphere during the period under study, and to compare their varying centrality across corpora. In this study, two well-established centrality metrics were focused on: degree and betweenness centrality. **Degree centrality** refers to the number of edges a node has. In this context, it indicates the number of documents in which a person was mentioned during the study period, or conversely, the number of persons mentioned in a given document. **Betweenness centrality** is a measure used in network analysis to quantify the importance or influence of a node within a network. It is based on the idea that a node is central if it lies on a large number of shortest paths between other pairs of nodes in the network. Nodes with high betweenness centrality act as bridges or intermediaries, facilitating communication and information flow between other nodes. Betweenness centrality is a useful complement to degree centrality, particularly helpful in filtering out "background personalities" such as Jiang Jieshi, Roosevelt, or Hitler, who were frequently mentioned in the press but were not directly connected to Rotary Club’s activities. Background personalities generally exhibit a high degree but comparatively low betweenness centrality in the Rotary network.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The results are described and interpreted in the following narrative layers. *Note: The numbers indicated within parentheses below refer to the unique document identifier (DocId) used in the Modern China Textbase (MCTB) accessible through [HistText](https://bookdown.enpchina.eu/HistText_Book/set-up.html#available-corpora).*
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
### Building International Peace through Youth and Education (1919-1929)
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
#### Topics
<!-- #endregion -->

The Chinese and English press shared a number of similar concerns (refer to [table 13](#anchor-table-13)). Both demonstrated a strong interest in youth and education, though this focus was statistically more significant in the Chinese press (41%, compared to 31% in the foreign press), and their perspectives differed. While *Shenbao* emphasized educational activities in China, such as the Boy Scout meetings sponsored by the Rotary Club (SPSP192810141212, SPSP192810021501) and American students in China, such as the students from the US Maritime Academy (Meiguo Haishang daxue 美國海上大學) who visited Shanghai in January 1929 (SPSP192901121101), the English-language press emphasized reversed flows from China to the United States. They reported on the students of Shanghai American schools who received Rotary bursaries to study in America (1324671546) and featured biographies of Chinese individuals educated in the United States. The post-WWI period coincided with the first large batches of students returning from the United States since the recall of the aborted Chinese Educational Mission (1872-1881), and some of these students were beginning to take positions of influence in China. Examples include Kuang Fuzhuo 鄺富灼 (1869-1938), a graduate of Columbia University who became president of the Shanghai Rotary Club in 1929 (1321529215, 1420023531), Niu Huisheng 牛惠生 (1892-1937), a Harvard graduate and orthopaedic specialist (1319868907), or the Chinese members of the Shanghai Municipal Council elected in 1928 (1371312334). While both presses portrayed the returned students as agents of international friendship, the English press viewed them as a factor of progress and political stability in China (1324748781, 1321417206), whereas *Shenbao* adopted a more pragmatic stance, viewing their foreign education primarily as a tool for building business relations between China and the United States (SPSP192901121101).


Both corpora shared a similar concern for international peace and cooperation, which was a core principle in the Rotary philosophy and represented in similar proportions in the two corpora (37-38%). This international awareness manifested through banquets and ceremonies aimed at celebrating international friendship, as well as lectures given by Rotary leaders, representatives of the League of Nations (1322096569), and scholars specializing in political sciences and international relations (1324748781, 1321227034, 1321249158). In *Shenbao*, two key events were extensively covered during this period: the Rotary Pacific Conference that took place in Tokyo in October 1928 (SPSP192810020903, SPSP192810171501, SPSP192811091505), and the International Day held in Shanghai in December 1929 under the auspices of the Rotary Club (SPSP192912201501, SPSP192912201513).


Interestingly, youth was perceived as a key factor in the realization of world peace. The International Day mobilized ten children from ten different countries who presented the national emblem of their respective home country. The two events provided opportunities to emphasize international friendship and harmony among nations. There were subtle differences, however, in how the topic of international peace was framed in each corpus. Whereas *Shenbao* tended to emphasize its positive aspect, the English press adopted a more critical, if not pessimistic standpoint. Several articles emphasized the unsportsmanlike attitude of Japanese athletes at the Far Eastern Olympics held in Manila in 1934 (1425412837). In his lecture on the Institute of Pacific Relations given in 1927, for example, British official and journalist Frederick Whyte (1883-1970) highlighted the risks that uneducated public opinion created for world peace and political stability (1321227034, 1321249158). At the local level, Hu Hongdi, an expert in bacteriology for the Bureau of Public Health of the Municipality of Greater Shanghai, regretted the failed cooperation between Chinese and foreign municipal administrations towards the promotion of public health in Shanghai (1324685875).


Another difference lies in the forms that transnationalism took in the two corpora. The English press highlighted formal channels of diplomacy and international relations (topics 4 and 5), centered on the League of Nations (1322096569) and high officials, such as Chinese diplomat Shi Zhaoji 施肇基 (1877-1958) (1319919770) or foreign adviser to the Chinese government Westel Woodbury Willoughby (1319895153). By contrast, the Chinese press placed a stronger emphasis on informal networks of cooperation across national boundaries (topic 3). In 1928, for instance, *Shenbao* reported extensively on the business delegation from Honolulu aimed at fostering tourism and economic cooperation between China and Hawaii (SPSP192810131511). It regularly covered individual foreign visitors’ tours in China, such as world-renown pastor Sherwood Eddie (SPSP192211171601) and Suzhou-born American businessman Fei Wusheng 費吳生, who returned with the promise to raise funds from the Rockefeller foundation to establish a local Chinese branch of the Young Men’s Christian Association (YMCA) in Shanghai (SPSP192306131801). Each time a foreign visitor or delegation was expected, students’ associations, YMCA, and business organizations joined hands to organize banquets, tea parties, visits of local monuments, factories, and universities to entertain their guests. These transnational exchanges reveal an intriguing interconnection between business, education, and Christianity, with foreign-educated Chinese serving as cultural brokers.


The English press was particularly concerned with labor issues during this period, focusing on three key debates: the widespread labour strikes in China and Hong Kong in the early 1920s, the issue of child labour in the mid-1920s, and labor conditions in the Soviet Union in the late 1920s. The labour strikes in the early 1920s raised significant concerns among industrial elites in China, leading to extensive studies by sociologists and economic experts. American-educated Chinese journalist Dong Xianguang 董显光 (1887-1971) and American economist Charles Remer, invited to share their insights on the Chinese labour movement, advocated for the adoption of labour standards in China. They portrayed Rotary members and cotton magnates Nie Qijie 聶其傑 (1880-1953) and Mu Xiangyue 穆湘玥 (1876-1942) as exemplary capitalists who had anticipated workers' demands and taken preventive measures to enhance their social welfare, such as introducing sanitary facilities and providing education and entertainment for factory workers and their families (1319935662, 1319882138). Debates surrounding child labour in China gained prominence after the visit of Agatha Mary Harrison (1885–1954), an English industrial welfare reformer, to China in 1920 to investigate local industrial conditions. Her visit not only highlighted the issue of child labour but also criticized industrial exploitation by foreign powers as the main catalyst for turmoil in China. This perspective faced strong opposition from the British newspaper *North-China Herald* (1369965739, 1426577431). The aftermath of the Bolshevik revolution in October 1917 led Western observers to closely monitor the situation in the Soviet Union, apprehensive about the potential spread of communism in Europe and beyond. There was growing concern among foreigners residing in China that the extensive labour strikes in both China and Hong Kong might escalate into a broader social movement, potentially leading to a political revolution similar to the Bolshevik revolution. These anxieties intensified with the establishment of the first Chinese Communist Party (CCP) in Shanghai in 1921 and the formation of the United Front in 1924 between the CCP and the Guomindang (GMD) or Nationalist Party, which began receiving material aid and support from Soviet Russia to overthrow the warlords and imperialist powers in China. Foreign journalists closely followed the developments in Soviet Russia, considering it a testing ground or a potential scenario for the young and politically unstable Chinese Republic, and were invited to share their perspectives with Rotarians in China.

<!-- #region citation-manager={"citations": {"": []}} -->
Similarly, topics related to water conservancy and public health, with a particular focus on Tianjin and Shanghai, were predominantly covered in the foreign press (topic 3). English periodicals reported on the interest of business elites in the restoration of the deteriorated Grand Canal, seen as a means to stimulate trade in northern China and revitalize Tianjin's economy, a major port in the region. Although the project eventually failed due to financial troubles and factional struggles (<cite data-cite="626961/4ZWEG62G"></cite>, p. 53-79), the Rotary Club played a key role as a platform for garnering support and funding from northern elites. Figures like Yang Baoling 楊豹靈 (1886-1966), chief engineer in the Zhili River Commission, and former premier Yan Huiqing 顏惠慶 (1877-1950), a staunch supporter of the project, were invited to Rotary clubs in Tianjin and Beijing to promote the initiative before local elites, aiming to gain independence from global finance (1321449568, 1321539593, 1420021095). Finally, both corpora reflected Rotarians' concern with public health, but this focus was more pronounced in the foreign press (topic 3). While the *China Weekly Review* highlighted the efforts of the Shanghai Municipal Council (SMC) Public Health Department (1319876038), the *Shenbao* chose to cover the large-scale smallpox vaccination campaign sponsored in 1926 by the Rotary Club, along with other medical and voluntary associations. This choice might be attributed to the fact that smallpox primarily affected the Chinese population (SPSP192610311801).
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Five most prominent topics in the Shenbao and ProQuest corpora during the first period (1919-1929). The table indicates the language of the corpus, the topic number, a short label with a brief description of the topic, topic proportion, and the list of terms defining the topic. Frequency measures are based on simple frequency and FREX (Fully, Rank-Weighted Expected), two common measures calculated with the stm package. The frequency measure simply counts the number of times a term appears in the corpus, whereas FREX combines both the frequency and uniqueness of terms. The former provides a basic representation of the term's occurrence without considering its uniqueness or importance relative to other terms, while the latter penalizes terms that are too common or too rare and gives higher scores to terms that are moderately frequent and distinctive."], "type": "table"}} tags=["hermeneutics", "table-13", "anchor-table-13"] -->
| **Language** | **Topic** | **Label**                           | **Description**                                                            | **Proportion** | **Prob**                                                                                            | **Frex**                                                                                              |
|--------------|-----------|-------------------------------------|----------------------------------------------------------------------------|----------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Chinese      | 1         | Youth/Health                        | YMCA exhibition                                                            | 0.165          | 展覽會, 出品, 少年, 陳列, 展覽, 愛物, 北平, 四川, 中西, 時期                                        | 展覽, 愛物, 四川, 科學, 出品, 展覽會, 陳列, 少年, 北平, 國貨                                          |
| Chinese      | 2         | Sino-US exchanges                   | Sino-US cooperation                                                        | 0.206          | 情形, 美國, 禮查, 人民, 議決, 政府, 辦理, 公開, 可邀, 東方                                          | 人民, 議決, 政府, 辦理, 東方, 名人, 情形, 今午, 南美, 報云                                            |
| Chinese      | 3         | Transpacific networks               | Transpacific exchanges                                                     | 0.102          | 青年會, 學生, 十一時, 半開, 南洋, 工廠, 青年, 洋行, 遠東, 領袖                                      | 半開, 南洋, 工廠, 青年, 聖約翰, 交誼會, 個人, 列度者, 聖經, 青年會                                    |
| Chinese      | 4         | International peace                 | International peace                                                        | 0.276          | 國際, 日本, 國徽, 宗旨, 檀香山, 親善, 呈獻, 太平洋, 輪船, 時期                                      | 國徽, 呈獻, 太平洋, 輪船, 和平, 會務, 代表團, 聯合會, 國際, 十餘歲                                    |
| Chinese      | 5         | Boyscout/Education                  | Boyscouts and overseas students                                            | 0.252          | 童子軍, 世界, 美國, 汽車, 本報, 登君, 禮查, 狀况, 婦女, 職員                                        | 汽車, 醫院, 童子軍, 宣佈, 骨科, 登君, 本報, 世界, 狀况, 一九二                                        |
| English      | 1         | American education                  | Education and scholarship                                                  | 0.311          | american, school, peking, association, service, foreign,   commerce, university, committee, chamber | college, chamber, school, english, indemnity, editor,   university, manager, commerce, boxer          |
| English      | 4         | Pacific relations                   | Philippines and US policy in the Pacific                                   | 0.184          | government, states, united, japan, people, political, cable,   philippines, american, japanese      | cable, philippines, americans, radio, liberty, rights, japan,   civil, united, services               |
| English      | 5         | International peace                 | League of Nations, international peace and public health                   | 0.182          | nations, world, international, foreign, league, peace, public,   settlement, local, health          | nations, league, peace, international, spirit, institute,   relations, persons, settlement, council   |
| English      | 3         | Water conservancy and public health | Water conservancy and public health (with a particular focus   on Tianjin) | 0.166          | tientsin, river, water, conditions, health, commission, north,   disease, scheme, foreign           | river, tientsin, water, disease, scheme, conservancy,   diseases, connected, light, roads             |
| English      | 2         | Labor, industry, and Soviet Russia  | Labor, industry, and Soviet Russia                                         | 0.157          | labor, country, economic, people, conditions, industrial,   russian, russia, industry, revolution   | russian, labor, economic, production, industrial, laborers,   revolution, soviet, industry, communist |
<!-- #endregion -->

#### Persons


From the list of individuals identified through named entity recognition (NER), three primary categories of persons can be distinguished: (1) Rotary members and leaders, who were the most frequently mentioned; (2) guest speakers and external visitors, whose appearances were more exceptional, often limited to a single occurrence; and (3) local personalities or honorary members, who are less frequent than Rotarians but more frequent than external visitors. This differentiation is visible in the network of persons and documents built from the *Shenbao* newspaper ([figure 15](#anchor-figure-15)). The graph is neatly split into two distinct components: on the one hand, a large component populated with regular Rotary members and officers, and on the other hand, a smaller component composed of non-members who co-organized events with the Rotary Club, generally involving youth and business associations. Besides these two components, a myriad of small, isolated components involved special guests and exceptional visitors who clustered around a single document.

```R jdh={"object": {"source": ["Two-mode networks of persons and documents in *Shenbao* during the first period (1919-1929). Red squares represent documents, orange circles represent persons. The graph was constructed using the igraph R package (layout: Fruchterman-Reingold)."], "type": "image"}} tags=["figure-15", "anchor-figure-15"]
library("IRdisplay")
display_jpg(file="./media/Fig15_labels.JPG")
```

In terms of degree centrality, the most central actors were Rotary leaders, particularly the club’s presidents ([table 14](#anchor-table-14), [table 15](#anchor-table-15)). This should not come as a surprise, as they presided over every Rotary meeting, introduced guests and programs, and were invited to represent the club at external events such as Boy Scout and business gatherings. The most central person in the two corpora, in terms of both degree and betweenness centrality, was Kuang Fuzhuo, mentioned earlier. Kuang appeared throughout the entire decade and was associated with a wide range of topics, serving as a bridge between different communities of topics and actors. Specifically, he was mentioned for his participation as a delegate at the Rotary Convention in Manila in 1922 (1369499644), for inviting US Senator Hiram Bingham during his visit to China in August 1927 (1420021041), for his election to the position of vice-president and eventually president of the Shanghai Rotary Club in 1929, and his retirement from the Commercial Press in 1929 (1420023531).

<!-- #region citation-manager={"citations": {"": []}} -->
Other prominent Rotarians who appeared in the two corpora include Li Yuanxin 李元信 (William Yinson Lee), chairman of the program committee, who made notable efforts to “sinicize” the club by organizing special "Chinese programs" (<cite data-cite="626961/4YPDTCZE"></cite>). During this period, he was particularly interested in public health issues, organizing lectures on lepers (1321998956) and bubonic plague (1322040076). In contrast to their prominence in the English press, the first presidents of the club, American doctor Julian Petit and Chinese industrialist Zhu Shen'en 朱神恩 (Luther Jee), were not mentioned in *Shenbao*. This reflects the limited coverage the Rotary Club received in the Chinese press until Wang Yingbing 汪英賓 joined the club in the mid-1920s as the first representative of *Shenbao* and the official Rotary reporter.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
Conversely, *Shenbao* featured Chinese members of the local business community who remained hidden in the foreign press. These Chinese personalities appeared as guests during Rotary meetings and sponsored various events related to education, business, and public health. For example, the leading industrialist Liu Hongsheng 刘鸿生 (1888-1956), known as the “King of Matches” and the “King of Wool” (<cite data-cite="626961/9LMCR9XI"></cite>), appeared several times in 1928, although he joined the club only in 1930. Although they were not members of the club, Xu Zicheng 徐子成 and Yu Kuiyuan 余魁元, two educators involved in the Chinese Boy Scout movement, were connected to Rotary through their participation in joint events, such as fundraising campaigns and inter-school competitions.
<!-- #endregion -->

More generally, the Chinese press granted greater agency to Chinese actors, whereas foreign elites (local officials, diplomats, missionaries) were more central in the English press. Only two foreigners, US Consul Edwin Cunningham (Ke Yinhan 克銀漢, 1858-1953) and British entrepreneur G.E. Marden (Ma Dengjun 馬登君), manager of the eponymous company, were quite prominent in the two corpora. Marden served as the club president in 1928-1929, and Cunningham was invited to participate in several special events organized by the Rotary Club, such as the welcome reception in honour of US Senator Hiram Bingham in 1927 (SPSP192708051409).

<!-- #region jdh={"object": {"source": ["Most central persons in the two-mode networks of persons and documents in the Shenbao corpus during period 1 (1919-1929), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-14", "anchor-table-14"] -->
| **Name** | **Pinyin**     | **Degree** | **Betweenness** |
|----------|----------------|------------|-----------------|
| 鄺富灼   | Kuang Fuzhuo   | 6          | 0.5322824563    |
| 汪英賓   | Wang Yingbin   | 5          | 0.29536237      |
| 馬登君   | Ma Dengjun     | 5          | 0.2741735312    |
| 李元信   | Li Yuanxin     | 4          | 0.1442258441    |
| 徐子成   | Xu Zicheng     | 3          | 0.5685483871    |
| 牛惠生   | Niu Huisheng   | 2          | 0.2197307101    |
| 歐偉國   | Ou Weiguo      | 2          | 0.1359863466    |
| 余魁元   | Yu Kuiyuan     | 2          | 0.0846774194    |
| 劉鴻生   | Liu Hongsheng  | 2          | 0.0726503262    |
| 李登輝   | Li Denghui     | 2          | 0.0726503262    |
| 朱錫年   | Zhu Xinian     | 2          | 0.0625          |
| 克銀漢   | Ke Yinhan      | 2          | 0.0453174463    |
| 夏鵬     | Xia Peng       | 2          | 0.0249074237    |
| 王正廷   | Wang Zhengting | 2          | 0.0236583789    |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central persons in the two-mode networks of persons and documents in the ProQuest corpus during the first period (1919-1929), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-15", "anchor-table-15"] -->
| **Name**           | **Degree** | **Betweenness** |
|--------------------|------------|-----------------|
| Fong Foo-Sec       | 9          | 0.1064320161    |
| Wang               | 7          | 0.1377054756    |
| George Fitch       | 6          | 0.1871067167    |
| Julian Petit       | 6          | 0.103467284     |
| Stirling Fessenden | 5          | 0.0945416007    |
| William Yinson Lee | 5          | 0.0822077867    |
| Edwin Cunningham   | 5          | 0.0820320185    |
| Jabin Hsu          | 5          | 0.0615231384    |
| Luther Jee         | 5          | 0.060361723     |
| Wu Pei-Fu          | 4          | 0.0471230064    |
| Hiram Bingham      | 4          | 0.0380058885    |
| Kato               | 4          | 0.0329666418    |
| Marden             | 4          | 0.0267799377    |
| Julean Arnold      | 4          | 0.0230686328    |
| Wilson             | 4          | 0.0211698454    |
| Charles Dailey     | 4          | 0.0087421307    |
<!-- #endregion -->

#### Organizations

<!-- #region citation-manager={"citations": {"": []}} -->
Reflecting the topical emphasis on youth and education during this period, education-oriented institutions held a prominent position in both presses, particularly in *Shenbao*. In the Chinese newspaper, the most central organization in terms of betweenness centrality was the Young Men’s Christian Association (YMCA), a Protestant organization that aimed to spread the social gospel and promote education throughout the world. Introduced in China in 1885, it comprised 176 local branches spread across 16 provinces, representing about 50,000 members in the 1920s (<cite data-cite="626961/S6H6G6WJ"></cite>, p.20). Urban business and professional elites, regardless of their religious beliefs, actively participated in the movement, as previous research has shown (<cite data-cite="626961/K3ED2GLE"></cite>, chapter 3). Many Rotarians, both Chinese and foreign, were concurrently members of the YMCA. The two organizations frequently organized joint events dedicated to youth and education, such as inter-school competitions, Boy Scout meetings, or educational exhibitions.
<!-- #endregion -->

Universities, particularly American-run or American-inspired universities, also featured prominently in *Shenbao*. They notably included St. John’s University, a missionary institution established in 1879 by American Protestants in Shanghai, and Yanjing University in Beijing, which was formed between 1915-1920 from the merger of several Christian schools and established a partnership with Harvard University. Both St. John’s and Yanjing were among the first institutions to teach foreign languages and sciences in China and attracted many students from Chinese elite families, especially those who aimed to pursue further studies abroad. As shown in previous research, many Rotarians had studied or were teaching in these universities and maintained contact with professors in these institutions whom they invited to give lectures before Rotary members, such as Xing Weilian 興煒蓮, the director of academic affairs at Yanjing University (SPSP192807131501).

<!-- #region citation-manager={"citations": {"": []}} -->
While alumni associations appeared in both presses, *Shenbao* more often featured Chinese-born organizations, such as the Western Students’ Association (OuMei liuxuesheng 歐美留學生會), whereas English periodicals highlighted members of the American University Club, which was established by Americans in Shanghai around 1902 and became the largest alumni association for graduates of American universities in China (<cite data-cite="626961/V8XIYBR6"></cite>). Many Rotarians who had studied abroad were concurrently members of these associations. As shown earlier, students’ associations and Rotary clubs frequently co-organized events, such as welcome receptions for prominent foreign guests and students’ or business delegations from abroad.
<!-- #endregion -->

The Shanghai Municipal Council (SMC) played a central role in both corpora. Established in 1854 to govern the daily operations and infrastructure of the Shanghai International Settlement, it became an indispensable institution for both foreign and Chinese elites residing and working in the International Settlement. These elites were concerned with maintaining favourable economic and social conditions in the settlement. The missions of the SMC aligned with Rotary’s interests in public health and social welfare in the city. Several representatives of the SMC were concurrently members of the Rotary Club or maintained personal contacts with the Rotary Club, frequently participating in Rotary meetings.

<!-- #region citation-manager={"citations": {"": []}} -->
Reflecting its emphasis on internationalism and international relations, as noted earlier, the foreign press gave prominence to international organizations, specifically the League of Nations, foreign government agencies (such as the US Congress and Senate, British Foreign Office), and Sino-foreign institutions like the British Boxer Indemnity Commission. The latter was a bilateral Sino-British committee established in 1926 to devise a proposal for allocating funds derived from the remission of the British Boxer Indemnity (<cite data-cite="626961/BL6BQ7ZJ"></cite>, forthcoming). Similarly, the Zhili River Commission, largely funded with American and other foreign funds, was mentioned in connection with topic 3 (<cite data-cite="626961/4ZWEG62G"></cite>, p. 53-79).
<!-- #endregion -->

In contrast to *Shenbao*, which focused on local, non-state organizations, the foreign press placed a stronger emphasis on central government institutions in China, reflecting foreign concerns for China’s political stability during the so-called warlord era (1916-1927). The Chinese government during this period alternated between the Beiyang government in Beijing (1912-1928) and, from 1927 onwards, the Nationalist government established in Nanjing. The Chinese government primarily appeared as a "background" institution often mentioned in lectures given before Rotary members. It was also mentioned in connection with government personalities who were occasionally invited as guests to participate in Rotary meetings, despite the self-claimed "apolitical" nature of the Rotary Club. Despite its low degree centrality, the Bureau of Economic Information (BEI) held an important brokering position in the foreign press, particularly due to its concern with labour strikes in 1922. Established in 1921 by the Ministry of Industry, the BEI produced a series of extensive surveys on the labour movement, serving as a primary source of information for Rotary members and lecturers on this topic.

<!-- #region jdh={"object": {"source": ["Most central organizations in the two-mode networks of persons and documents in the Shenbao corpus during the first period (1919-1929), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-16", "anchor-table-16"] -->
| **Name**       | **Pinyin**                    | **Transliteration**                   | **Degree** | **Betweenness**       |
|----------------|-------------------------------|---------------------------------------|------------|-----------------------|
| 扶輪社         | Fulunshe                      | Rotary Club                           | 50         | 0.8372544541          |
| 上海扶輪社     | Shanghai Fulunshe             | Shanghai Rotary Club                  | 22         | 0.2494076356          |
| 青年會         | Qingnianhui                   | YMCA                                  | 5          | 0.0268094625          |
| 天津扶輪社     | Tianjin Fulunshe              | Tianjin Rotary Club                   | 3          | 0.0175438596          |
| 工商部         | Gongshangbu                   | Shanghai Municipal Council            | 3          | 0.0021411659          |
| 衞生教育會     | Weisheng jiaoyuhui            | Health Education Association          | 2          | 6.247262797228017E-4  |
| 上海青年會     | Shanghaiqing nianhui          | Shanghai YMCA                         | 2          | 3.512987514842373E-5  |
| 南洋大學       | Nanyang daxue                 | Nanyang University                    | 2          | 3.512987514842373E-5  |
| 歐美留學生會   | OuMei liuxuesheng             | Western Returned Students Association | 2          | 3.512987514842373E-5  |
| 浦東青年會     | Pudong Qingnianhui            | Pudong YMCA                           | 2          | 3.512987514842373E-5  |
| 聖約翰大學     | ShengYuehan daxue             | St John's University                  | 2          | 3.512987514842373E-5  |
| 青年協會       | Qingnian xiehui               | YMCA National Committee               | 2          | 3.512987514842373E-5  |
| 青年會聖經學校 | Qingnianhui Shengjing xuexiao | YMCA Bible School                     | 2          | 3.512987514842373E-5  |
| 青年會職工部   | Qingnianhui zhigong bu        | YMCA Workers' Department              | 2          | 3.512987514842373E-5  |
| 上海童子軍     | Shanghai tongzijun            | Shanghai Boy Scouts                   | 2          | 3.4778576396939483E-4 |
| 檀香山扶輪社   | Tanxiangshan Fulunshe         | Honolulu Rotary Club                  | 2          | 2.552410621040343E-4  |
| 聯青社         | Lianqing she                  | Y's Men's Club                        | 2          | 1.5457145065306434E-4 |
| 國際扶輪社     | Guoji fulunshe                | Rotary International                  | 2          | 0.0174665739          |
| 大陸報         | Dalubao                       | China Press                           | 2          | 0.0054392419          |
| 燕京大學       | Yanjing Daxue                 | Yenching University                   | 2          | 0.0044071307          |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central organizations in the two-mode networks of persons and documents in the ProQuest corpus during the first period (1919-1929), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-17", "anchor-table-17"] -->
| **Name**                                | **Degree** | **Betweenness** |
|-----------------------------------------|------------|-----------------|
| Rotary Club                             | 103        | 0.6493214601    |
| Shanghai Rotary Club                    | 50         | 0.2235283847    |
| Chinese Government                      | 20         | 0.0678455115    |
| League Of Nations                       | 16         | 0.1312887807    |
| Shanghai Municipal Council              | 13         | 0.0537046705    |
| American University Club                | 12         | 0.033781378     |
| Tientsin Rotary Club                    | 11         | 0.025427715     |
| United States Congress                  | 7          | 0.0116964809    |
| Commercial Press                        | 7          | 0.0087825663    |
| Kuomintang                              | 7          | 0.0075066588    |
| Senate                                  | 6          | 0.0093169649    |
| United States Government                | 6          | 0.0083113874    |
| American Chamber Of Commerce   Of China | 6          | 0.0046673955    |
| Peking Rotary Club                      | 5          | 0.013001314     |
| Harvard University                      | 5          | 0.0121577714    |
| Foreign Office                          | 5          | 0.0119604198    |
| Institution For The Chinese   Blind     | 5          | 0.0103201874    |
| Chicago Tribune                         | 5          | 0.0051116055    |
| Pan-Pacific Association                 | 4          | 0.0041689955    |
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
### Handling Economic Crises, Social Unrest, and Mounting International Tensions (1930-1937)
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
#### Topics
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
The second period is characterized by a greater convergence between the two corpora in terms of both topics and actors. In the 1930s, international relations remained a prominent topic in both presses. In *Shenbao*, this topic centred on Chinese diplomat Wang Zhengting 王正廷 (1882-1961) who became a key player in both Rotary International and Sino-US diplomatic relations during this decade. Wang was minister of foreign affairs until 1936, when he was simultaneously appointed governor of the 81st district of the Rotary Club (which covered China, Hong Kong, and the Philippines) and Chinese ambassador to the United States. In the English press, concerns with international relations focused on the Japanese imperialist expansion in Asia and growing tensions between competing powers (Japan, United States, and Russia) for controlling the Pacific area.
<!-- #endregion -->

Following the 1929 crisis and the global depression which reached China around 1933, the decade was shaped by a new attention towards economic issues. The English press adopted an external, global perspective focused on three key debates: tariff reform in 1931 (1418906192, 1419818815), silver crisis and currency reform in 1933-1934 (1371489381), Chinese foreign trade in 1935-1936 (1371415865, 1371887425). By contrast, *Shenbao* was more concerned with the local effects of global crisis, as reflected in Wu Tiecheng 吳鐵城’s talk on Shanghai’s “strange prosperity” (*Qiguai de fanrong* 奇怪的繁榮) in 1934 (SPSP193406231519), and internal economic development propelled by railway construction, such as in Northwest China, the new frontier envisioned by Qingdao Mayor Shen Honglie 沈鴻烈 to counteract the Japanese occupation of Manchuria (SPSP193602120601) or highway construction aimed at developing tourism in Hangzhou (SPSP193511040916). The emphasis on the business and human networks underlying economic flows and pragmatic actions was another distinct feature of the Chinese daily, whereas the English press featured extensive reports of scholarly lectures by eminent economists or experts in foreign trade, such as Austrian financial expert Eduard Kann (1880–1962) (1371489381), Chinese economist He Lian 何廉 (Franklin Ho, 1895-1975) (1371776996), and American commercial attaché Julean Arnold (1875-1946) (1371415865, 1371887425).  

<!-- #region citation-manager={"citations": {"": []}} -->
Education and youth were losing ground, whereas social affairs, particularly labour issues, were gaining momentum as side effects of the economic crisis. In the English press, these issues revolved around the rickshaw reforms following the 1934 survey aimed at improving pullers’ living conditions (1416479521, 1371489587, 1371428577, 1425424004). In *Shenbao*, the attention was focused on various social affairs. Public health was a growing concern in the two presses. This concern resulted from the combination of three main trends: the epidemic threats revived by the influx of refugees from North-eastern China after the Japanese invasion of Manchuria in September 1931, the professionalization of Chinese medicine, and the dominance of medical professionals among Rotarians (<cite data-cite="626961/4YPDTCZE"></cite>). However, the focus and perspective differed across languages. Similar to economic affairs, English periodicals accommodated extensive reports of scholarly lectures given by foreign or foreign-educated Chinese experts in medicine and public health, such as Edward H. Hume (1876-1965), founder of the Yale hospital and former director of Yale-in-China in Changsha, Hunan (1416488362). By contrast, the daily *Shenbao* privileged a pragmatic stance emphasizing the private initiatives of local elites and voluntary organizations for promoting public health, notably through the establishment of the anti-tuberculosis association in 1931 (SPSP193303290901) or the petition for the protection of lepers from military exactions in 1937 (SPSP193704261001).      
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Five most prominent topics in the Shenbao and ProQuest corpora during the second period (1930-1937)."], "type": "table"}} tags=["hermeneutics", "table-18", "anchor-table-18"] -->
| **Language** | **Topic** | **Label**                                       | **Description**                                                                                                                                                                               | **Proportion** | **Prob**                                                                                         | **Frex**                                                                                       |
|--------------|-----------|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Chinese      | 1         | Business & transnational networks               | Transnational business connections                                                                                                                                                            | 0.147          | 商業, 本月, 歐洲, 四時, 和平, 起見, 商會, 學生, 發起, 國際                                       | 商業, 歐洲, 和平, 商會, 學生, 本月, 四時, 歡宴, 倫敦, 起見                                     |
| Chinese      | 2         | International relations/Wang Zhengting          | International relations & Wang Zhengting                                                                                                                                                      | 0.249          | 國際, 美國, 英國, 世界, 夫人, 香港, 南京, 王正廷, 職業, 遠東                                     | 香港, 美國, 南京, 予以, 夫人, 國際, 職業, 外交, 法國, 英國                                     |
| Chinese      | 3         | Transportation and economic development         | Transportation and economic development                                                                                                                                                       | 0.187          | 日本, 汽車, 杭州, 兒童, 交通, 北平, 經濟, 天津, 講演, 小時                                       | 日本, 汽車, 杭州, 兒童, 交通, 天津, 講演, 小時, 時間, 華人                                     |
| Chinese      | 4         | Tennis Cup & Sports                             | Tennis and sports competitions                                                                                                                                                                | 0.199          | 比賽, 萬國, 網球, 錦標, 中華, 盛大, 表演, 大華, 體育, 捐助                                       | 比賽, 網球, 錦標, 表演, 大華, 萬國, 跳舞, 紀念, 於今, 盛大                                     |
| Chinese      | 5         | Charity, public health, municipal admnistration | Charity & Public health                                                                                                                                                                       | 0.218          | 工作, 將來, 運動, 男女, 衛生, 贊助, 努力, 人民, 當局, 辦法                                       | 將來, 運動, 男女, 衛生, 贊助, 努力, 共同, 提倡, 研究, 維持                                     |
| English      | 4         | RI celebrations                                 | Rotary International celebration                                                                                                                                                              | 0.310          | nanking, international, local, service, american, university,   visit, foreign, national, party  | soochow, kulangsu, honorary, chicago, madame, christmas,   george, german, tsingtao, clock     |
| English      | 2         | Education, health, culture                      | Education, health and culture                                                                                                                                                                 | 0.195          | education, school, people, world, schools, system, women,   country, modern, young               | woman, disease, teaching, ideas, seconds, language, writing,   pictures, science, education    |
| English      | 1         | US-Japan-Pacific                                | US-Japan confrontation in Asia and the Pacific area (control   over Manchuria, Philippines, also involving Russia and the silver currency   problem).                                         | 0.187          | japanese, japan, world, silver, states, american, united,   people, america, nations             | silver, manchuria, philippine, russians, dairen, japan,   filipinos, russia, japanese, russian |
| English      | 5         | Economic and social affairs                     | Rickshaw problem in Nanjing and other social problems, issues   of urban management and the management of natural disasters such flood in   Shandong. Focus of interest between 1934 and 1937 | 0.172          | government, public, nanking, municipal, council, bureau,   river, roads, association, national   | pullers, rickshaw, ricksha, roads, river, municipal, relief,   owners, dykes, traffic          |
| English      | 3         | Economic and social affairs                     | China's foreign trade and economic development (first half of   the 1930s decade)                                                                                                             | 0.136          | trade, foreign, country, industry, economic, development,   world, goods, government, industrial | cotton, industry, tourist, trade, industries, goods,   production, materials, arnold, tourists |
<!-- #endregion -->

#### Persons


The prominent actors are consistent with the topical concerns of the decade. The most prominent persons were Rotarians involved the local organization of Rotary clubs in China and Asia. Their presence signalled the trend towards self-organisation and the indigenization of the movement, with Chinese actors becoming more central than during the previous decade, and some Chinese leaders like Wang Zhengting 王正廷 even gaining an influential position at the international level. High-ranking Rotary officers included Chinese presidents of the Shanghai Rotary Club (Kuang Fuzhuo 鄘富灼 and Zhu Boquan 朱博泉, 1898-2001) and district governors Kuang Fuzhuo and Wang Zhengting. The most frequently mentioned person in both corpora was Wang Zhengting, especially after his election as Rotary district governor and his appointment as Chinese ambassador to the United States in 1936. Despite having a lower degree centrality than Wang Zhengting, Kuang Fuzhuo showed a higher betweenness centrality, meaning that he continued to play a key bridging role between different topics and communities of actors until his death in 1938. The second group of prominent persons included local officials and business elites who appeared in connection with lectures addressing the economic development of their cities (Shanghai Mayor Wu Tiecheng 吳鐵城, Qingdao Mayor Shen Honglie 沈鴻烈) and the prosperity of the country at large. As these topics necessitated solving labour issues and promoting public health, they required the support of prominent industrialists and businesspeople such as Liu Hongsheng 劉鴻生 (1888-1956) or Wang Xiaolai 王曉籟 (1886-1967), who both participated in the inaugural meeting of the China Business Management Association (Zhongguo gongshang guanli xiehui 中國工商管理協會) (SPSP193007071401), as we elaborate below. They also involved public health experts, such as Wu Liande 伍連德 (1879-1960), director of the National Quarantine Service (Quanguo haigang jianyi zong guanlichu 全國海港檢疫總管理處) established in 1930 by the Nationalist government, who supported the creation of the anti-tuberculosis association (Fanglaohui 防癆會) in 1933 (SPSP193303281601) and gave various lectures on public health, including one advocating for cremation (SPSP193606201501).


Notorious foreigners were prominent in the English press. They principally included Rotary leaders, such as George Fitch, an American missionary born in Suzhou (1883-1979) who served as president of the Shanghai Rotary Club and later became vice-president of the Nanjing Rotary Club. The visit of Paul Harris (1868-1947), the “father” of the Rotary Club, who came to Shanghai to attend the annual convention held in 1936, was extensively covered in the foreign press (1371410985, 1416683178, 1371410985, 1420042137). His homonym E.F. Harris, another president of the Shanghai Rotary Club, was another key player during this decade. He notably participated in the delegation which attempted to mediate between Japan and China following the Japanese attack on Shanghai in 1932, and was highly critical of the laissez-faire attitude of Rotary International and foreign authorities towards the Japanese aggression. (1369970997). He later blamed the US economic policy of raising the world price of silver to help silver-producing states for having done as much damage to China as the war (1416529590). Other prominent persons in the foreign press included local officials such as US commercial attaché Julean Arnold (1875-1946), who was concurrently an honorary member of the Shanghai Rotary Club and gave several lectures on foreign trade, tourism, and similar topics.  

<!-- #region jdh={"object": {"source": ["Most central persons in the two-mode networks of persons and documents in the Shenbao corpus during the second period (1930-1937), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-19", "anchor-table-19"] -->
| **Name** | **Pinyin**     | **Degree** | **Betweenness**     |
|----------|----------------|------------|---------------------|
| 王正廷   | Wang Zhengting | 15         | 0.252688857287479   |
| 鄘富灼   | Kuang Fuzhuo   | 7          | 0.261097016983449   |
| 吳鐵城   | Wu Tiecheng    | 5          | 0.165566297081493   |
| 朱博泉   | Zhu Boquan     | 4          | 0.185005853617252   |
| 張竹平   | Zhang Zhuping  | 4          | 0.177796748812709   |
| 王曉籟   | Wang Xiaolai   | 4          | 0.0820663397860432  |
| 胡憲生   | Hu Xiansheng   | 4          | 0.0351693501659262  |
| 沈鴻烈   | Shen Honglie   | 4          | 0.017698804277211   |
| 柯立芝   | Ke Lizhi       | 4          | 0.0118780257785785  |
| 大衛生   | Da Weisheng    | 3          | 0.833333333333333   |
| 潘公展   | Pan Gongzhan   | 3          | 0.0549080300427227  |
| 鄒秉文   | Zou Bingwen    | 3          | 0.0254514729999011  |
| 劉鴻生   | Liu Hongsheng  | 3          | 0.0218397122955577  |
| 張祥麟   | Zhang Xianglin | 3          | 0.0218397122955577  |
| 徐寄廎   | Xu Jiqing      | 3          | 0.0218397122955577  |
| 王儒堂   | Wang Rutang    | 3          | 0.0118167611890506  |
| 哈雷斯   | Ha Leisi       | 3          | 0.00711978683175826 |
| 韓爾     | Han Er         | 3          | 0.00711978683175826 |
| 伍連德   | Wu Liande      | 3          | 0.00600056186680245 |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central persons in the two-mode networks of persons and documents in the ProQuest corpus during the second period (1930-1937), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-20", "anchor-table-20"] -->
| **Name**        | **Degree** | **Betweenness** | **Name**     | **Degree** | **Betweenness** |
|-----------------|------------|-----------------|--------------|------------|-----------------|
| Wang            | 54         | 0.17678938      | Cunningham   | 6          | 0.02413016      |
| Chen            | 19         | 0.10470646      | Percy Chu    | 14         | 0.02411009      |
| Harris          | 32         | 0.0995815       | Hans Berents | 14         | 0.02398223      |
| Wu              | 29         | 0.05677344      | Roosevelt    | 10         | 0.02255324      |
| George Fitch    | 34         | 0.05229355      | Arnold       | 15         | 0.02238264      |
| Lee             | 14         | 0.04020946      | Liu          | 11         | 0.02224333      |
| Smith           | 13         | 0.03795009      | Wilson       | 10         | 0.02166664      |
| Peiping         | 16         | 0.03531346      | Marsh        | 6          | 0.0200758       |
| Chiang Kai-Shek | 19         | 0.03371979      | Hoover       | 10         | 0.01965428      |
| Julean Arnold   | 19         | 0.03085069      | Johnson      | 9          | 0.01913842      |
| Ho              | 15         | 0.0283243       | Yen          | 11         | 0.01913618      |
| Fong            | 12         | 0.02586974      | Chang        | 13         | 0.01907477      |
| Zee             | 16         | 0.02506978      | Kwok         | 4          | 0.01877596      |
| Wentworth       | 5          | 0.02491093      | Yu           | 9          | 0.01855067      |
| Kung            | 11         | 0.02443583      | Morley       | 11         | 0.01703704      |
<!-- #endregion -->

#### Organizations


The 1930 decade was marked by the growing visibility of central government institutions, including the government itself, its various ministries (especially those related to industry, trade, and finance) and its bureaucratic organs. This shift primarily reflected the centralization of power during the Nanjing decade (1927-1937) following the establishment of the Nationalist government in 1927. With the rise of economic concerns during the 1930s, both the English- and Chinese-language presses recorded the growing centrality of economic-oriented institutions. A key institution during this period was the National Economic Council (Quanguo jingji weiyuanhui 全國經濟委員會) established in 1931 by the Nationalist Government to support infrastructural projects, such as railway construction in Northwest China. In the Chinese press, the National Economic Council (NEC) was also mentioned in connection with public health campaigns, specifically against leprosy (SPSP193704261001), which suggested that public health was recognized as a vital ingredient in economic prosperity.


While the English press focused on government institutions, the *Shenbao* devoted more attention to non-state institutions, such as the China Business Management Association (Zhongguo gongshang guanli xiehui 中國工商管理協會), an informal group of business and industrial leaders founded in Shanghai in July 1930 (SPSP193007071401). Although it was established at the initiative of the Minister of Industry and Finance Kong Xiangxi 孔祥熙 (1880-1967), the association was explicitly modelled after the Rotary Club and sought to mimic its practices in the form of luncheons and dinners. These entertaining venues, Kong believed, offered a favourable meeting ground for discussing crucial issues of the time, such as the currency crisis and the implementation of the new factory laws enacted in 1931 under the auspices of the League of Nations. The Bank of China 中國銀行 also featured prominently in the two corpora. It was a key interlocutor for international lenders and a crucial instrument for financing economic development and infrastructural projects planned by the NEC. It was mentioned in several lectures focused on analysing the economic situation and currency crisis in China in the 1930s.  The Bank of China was also the employer of several Rotary members, particularly those based in Nanjing.

<!-- #region citation-manager={"citations": {"": []}} -->
The League of Nations remained central in the foreign press and began to appear in the Chinese press as well. Besides being mentioned in lectures on international peace and economic or cultural development, the League became more active in China by sending several experts who were attached to the NEC, such as Stanislaw Okecki (1908-1991), a Polish expert who represented the League Transit Organization (1418985832), the French administrator Jean Monnet, who was sent to assist the Chinese Government in financing the economic reconstruction (1371468514), or William Kenneth Hunter Campbell, an expert on rural cooperatives (1371429509) (<cite data-cite="626961/UXTGDTKL"></cite>). Other international organisations, such as the Pan-Pacific Association (PPA), were more specific to the English press. Several Rotarians, such as Xu Jianping 許建屏 (Jabin Hsu, 1889-1968), were concurrently member of the PPA. The foreign press was eager to document PPA members’ decision to establish the National Good Roads Association (Zhonghua quanguo daolu jianshe xiehui 中華全國道路建設協會) to support road construction, perceived as a crucial vector of economic development (1371590314, 1371468514).
<!-- #endregion -->

At the local level, the Shanghai Municipal Council (SMC) was more central in the English press than in *Shenbao*. It refers to SMC officials who were invited by the Rotary Club of Shanghai to deliver lectures on their fields of expertise. More generally, the SMC was mentioned in speeches addressing social problems and issues of urban management in the International Settlement, such as rickshaw reforms in 1934, the housing crisis in 1935, road and traffic problems in 1934 and 1936, and other issues regarding public utilities. Interestingly, the SMC was increasingly referred to in comparison with the newly established Chinese municipality (1927), which aimed to stimulate a sort of competition or emulation between the two administrations. In his 1935 lecture, for instance, Pan Gongzhan 潘公展 (1895-1975), then Chinese commissioner of Social Affairs, overtly criticised the educational policy of the SMC and the system of selection in municipal schools based on social-economic background and political connections (1369972777).

<!-- #region citation-manager={"citations": {"": []}} -->
Like during the previous period, non-state institutions were more prominent in *Shenbao* than in the foreign press. The high betweenness centrality of Zhejiang University, notably, is intriguing and deserves closer examination. Zhejiang University is mentioned in connection with an American business delegation who visited China in 1935 (SPSP193506030901). As other similar delegations, the visitors were welcomed by local business elites and students’ associations, who organized various activities to entertain their guests. The schedule generally included a tour in Hangzhou, which was emerging as a key touristic destination during the Republican period (<cite data-cite="626961/6CKVX3QG"></cite>). Like the US Maritime students’ delegation during the previous period, this event highlighted the degree to which Sino-US business and academic networks were closely intertwined during this decade. Also remarkable is the high betweenness centrality of nation-based sports teams, particularly tennis and boxing teams. Against the backdrop of mounting international tensions, the Rotary Club promoted sports games as a pacific venue for fostering international friendship through friendly competition instead of wars and political tensions (SPSP193609161601). Business actors were also central to Rotary fundraising campaigns. Motorcar companies like Mark Moody (Madi qiche gongsi 馬迪汽車公司) contributed to charity events by offering attractive lots to motivate donations, such as free rides in brand new cars around Shanghai and even trips to Hollywood (SPSP193303081109).
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central organizations in the two-mode networks of persons and documents in the Shenbao corpus during the second period (1930-1937), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-21", "anchor-table-21"] -->
| **Name**         | **Pinyin**                       | **Transliteration**                   | **Degree** | **Betweenness** |
|------------------|----------------------------------|---------------------------------------|------------|-----------------|
| 扶輪社           | Fulunshe                         | Rotary Club                           | 87         | 0.8685054       |
| 靑島扶輪社       | Qingdao fulunshe                 | Qingdao Rotary Club                   | 3          | 0.8             |
| 上海扶輪社       | Shanghai fulunshe                | Shanghai Rotary Club                  | 32         | 0.2761449       |
| 國際扶輪社       | Guoji fulunshe                   | Rotary International                  | 12         | 0.0627398       |
| 浙江大學         | Zhejiang daxue                   | Zhejiang University                   | 2          | 0.0581537       |
| 萬國扶輪社       | Wanguo fulunshe                  | Rotary International                  | 5          | 0.0257706       |
| 全國經濟委員會   | Quanguo jingji weiyuanhui        | National Economic Council             | 3          | 0.0180965       |
| 中華隊           | Zhonghuadui                      | Chinese Team                          | 2          | 0.0151032       |
| 聯華總會         | Lianhua zonghui                  | United Chinese Associations           | 4          | 0.0129638       |
| 馬迪汽車公司     | Madiqiche gongsi                 | Mark Moody (automobile company)       | 2          | 0.0103137       |
| 外交部           | Waijiaobu                        | Ministry of Foreign Affairs           | 2          | 0.0093696       |
| 衛生局           | Weishengju                       | Bureau of Public Health               | 4          | 0.0092641       |
| 中國工商管理協會 | Zhongguo gongshang guanli xiehui | China Business Management Association | 3          | 0.0089828       |
| 中山醫院         | Zhongshan yiyuan                 | Zhongshan Hospital                    | 3          | 0.0080757       |
| 實業部           | Shiyebu                          | Ministry of Industry                  | 2          | 0.0064505       |
| 大來公司         | Dalai gongsi                     | Dah Lai Company                       | 4          | 0.0063908       |
| 上海國際扶輪社   | Shanghai guoji fulunshe          | Rotary International                  | 4          | 0.0062936       |
| 工部局           | Gongbuju                         | Shanghai Municipal Council            | 3          | 0.0060382       |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central organizations in the two-mode networks of persons and documents in the ProQuest corpus during the second period (1930-1937), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-22", "anchor-table-22"] -->
| **Name**                   | **Degree** | **Betweenness** | **Name**                   | **Degree** | **Betweenness** |
|----------------------------|------------|-----------------|----------------------------|------------|-----------------|
| Shanghai Rotary Club       | 157        | 0.28469367      | Ministry Of Communications | 8          | 0.0111046       |
| Chinese Rotary Club        | 2          | 0.125           | China Times                | 4          | 0.01075057      |
| Nanking Rotary Club        | 61         | 0.12399334      | Chamber Of Commerce        | 4          | 0.01052894      |
| League Of Nations          | 21         | 0.03619397      | National Economic Council  | 10         | 0.0101516       |
| Shanghai Municipal Council | 21         | 0.02121381      | Shanghai American School   | 4          | 0.0100959       |
| Congress                   | 6          | 0.02098699      | Central Government         | 6          | 0.00962554      |
| Peking Rotary Club         | 15         | 0.0188914       | Executive Yuan             | 10         | 0.00913067      |
| Bank Of China              | 14         | 0.01742312      | University Of Nanking      | 9          | 0.00911164      |
| Pan-Pacific Association    | 5          | 0.01703876      | Dairen Rotary Club         | 3          | 0.00900792      |
| Shanghai Telephone Company | 4          | 0.01668027      | International Club         | 9          | 0.00784739      |
| Kuomintang                 | 8          | 0.01602759      | Legislative Yuan           | 5          | 0.00781029      |
| National Government        | 11         | 0.01530957      | North-China Daily News     | 7          | 0.00778822      |
| Rotary International       | 26         | 0.01252879      | Shanghai Club              | 8          | 0.00732844      |
| China Press                | 7          | 0.01251597      | Peiping Rotary Club        | 5          | 0.00711427      |
| Customs                    | 17         | 0.01158434      | Ministry Of Industry       | 8          | 0.00703317      |
| Amoy Rotary Club           | 10         | 0.01110472      | Navy                       | 4          | 0.00679454      |
<!-- #endregion -->

### Wartime Survival and Post-war Reconstruction (1938-1949)


#### Topics


The two presses diverged again during the war and the post-war period. While international relations remained a central topic in both corpora, the English press adopted a high-level perspective, focusing on political economy and geopolitical tensions, such as Japan’s estrangement from the international system, disturbances to foreign trade, and currency issues in the post-war world. On the opposite, *Shenbao* focused on grassroots operations led by transnational or translocal forces to support the war effort and post-war reconstruction. These operations ranged from Rotary expansion in non-occupied China during the war and its division into subdistricts (SPSP194704130420), the reorganization of clubs after the war (SPSP194704130401, SPSP194704120401), the vital reliance on remittances from overseas Chinese in Malaya (SPSP194106070701), and China-Burma cross-border exchanges (SPSP193912150301, SPSP194109060601, SPSP194109050601). Maintaining good relationships with Burma through Chinese emigres in this country was crucial to ensure the chain of supply on the Burma Road linking Burma (now Myanmar) with southwest China. The Burma Road was built in 1937-1938 while Burma was a British colony to convey supplies to China during the Sino-Japanese War. In this context, the Rotary Clubs of Chongqing and Kunming served as key intermediaries, welcoming two delegations of Chinese business elites from Burma in 1939 and 1941.  

<!-- #region citation-manager={"citations": {"": []}} -->
In the English-language press, topics focused on political economy revolved around two sets of issues and events. During the war, a series of official speeches given during the early phase of the war (1938-1939), which culminated during the Foreign Trade Week held in Shanghai in 1940, aimed to celebrate and foster the continuation of Sino-American relations despite disturbances provoked by the war (1371507091). After the war, the foreign press reflected Chinese elites’ concerns regarding US policy of restoring Japan’s economy and industry against the backdrop of the emerging Cold War, which was perceived as a direct threat to their country’s national security (1371519387). Topics that were specific to the English press focused on Russian refugees, the prevention of venereal diseases, and other issues that were perceived as immediate threats to the well-being of foreign residents in Shanghai. Russian emigrates had been a constant concern in the foreign press since the October (1917) revolution, but this concern was heightened as Russians became the largest group of foreign residents in Shanghai and the arrival of war refugees increased the pressure (<cite data-cite="626961/TPUGQE3W"></cite>, 50-55).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
By contrast, the Chinese press was more concerned with entertaining underprivileged children for Christmas and building a “beggar camp” (Qigai shourong suo 乞丐收容所) in an attempt to eradicate poverty from Shanghai foreign settlements (SPSP194101220901). The so-called “beggars” in fact referred to the massive waves of people seeking refuge from the Chinese municipality and the north-eastern and eastern districts of the International Settlement, which were most exposed to war. At its highest point, the International Settlement harboured 160 camps with more than 90,000 refugees, while the French Concession’s dozens camps received 27,000 (<cite data-cite="626961/TPUGQE3W"></cite>, 84-86). This massive and sudden influx of refugees represented a significant challenge for both the local population and the municipal administrations. The idea of grouping the refugees into a single camp in preparation for their gradual evacuation came from the municipal authorities and local elite organizations like the Rotary Club. The proposed plan was financially supported by the Rotary Club of Shanghai and the SMC Public Works Department, while its management was entrusted to the Salvation Army (Jiushijun 救世軍) (SPSP194111040713, SPSP194101220901). Despite regular official reports that asserted that “beggary” was declining and that refugees were peacefully being sent back to their homes, the camp increased in scale and became a “beggar city” (Qigaishi 乞丐市) within a year, relocated in the Western outskirts of Shanghai (SPSP194110101113).
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Five most prominent topics in the Shenbao and ProQuest corpora during the third period (1938-1949)."], "type": "table"}} tags=["hermeneutics", "table-23", "anchor-table-23"] -->
| **Language** | **Topic** | **Label**                    | **Description**                                                                 | **Proportion** | **Prob**                                                                                            | **Frex**                                                                                              |
|--------------|-----------|------------------------------|---------------------------------------------------------------------------------|----------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Chinese      | 1         | Postwar reconstruction       | Postwar economic cooperation                                                    | 0.13           | 人民, 世界, 戰爭, 內地, 經濟, 影響, 國家, 合作, 目的, 戰後                                          | 人民, 戰爭, 內地, 國家, 世界, 經濟, 目的, 影響, 合作, 過去                                            |
| Chinese      | 2         | Beggar camp                  | Beggar camp                                                                     | 0.164          | 玩具, 兒童, 修理, 醫院, 破舊, 大戲院, 徵集, 南京, 運動, 加以                                        | 玩具, 兒童, 修理, 醫院, 破舊, 運動, 徵求, 汽車, 馬伯樂, 前來                                          |
| Chinese      | 3         | Movie                        | Movie to collect funds for poor children and other film   projections           | 0.157          | 乞丐, 收容所, 救世軍, 工部局, 收容, 計劃, 救濟, 租界, 情形, 人數                                    | 乞丐, 收容所, 救世軍, 工部局, 收容, 租界, 情形, 救濟, 計劃, 注意                                      |
| Chinese      | 4         | Toy collection               | Toy collection                                                                  | 0.215          | 苦兒, 電影, 影片, 放映, 記者, 節目, 發起, 時間, 儀式, 歡宴                                          | 苦兒, 電影, 影片, 放映, 記者, 節目, 時間, 儀式, 歡宴, 一六                                            |
| Chinese      | 5         | War/Postwar Rotary           | Wartime lectures and postwar reorganization of Chinese Rotary                   | 0.333          | 美國, 國際, 自由, 聽講, 邀同, 發展, 安全, 賓友, 預留, 興趣                                          | 美國, 國際, 自由, 聽講, 邀同, 安全, 賓友, 預留, 興趣, 蒞會                                            |
| English      | 4         | Japan                        | Japanese war propaganda                                                         | 0.239          | japanese, japan, american, united, press, foreign, tokyo,   military, record, authorities           | tokyo, japanese, press, record, japan, military, police,   authorities, consul-, nanking              |
| English      | 3         | Railways                     | Railways strategic importance in wartime and biographies of   railway engineers | 0.238          | hongkong, railway, school, university, college, province,   railways, government, education, middle | hongkong, college, railway, railways, middle, province,   university, miles, outside, school          |
| English      | 5         | Russians                     | Russian communities                                                             | 0.192          | russian, people, service, children, russia, business, bishop,   russians, local, death              | russian, bishop, russians, russia, business, german, children,   service, knowledge, germany          |
| English      | 1         | Postwar reconstruction       | War and postwar economy and sino-US trade relations                             | 0.185          | american, states, world, united, economic, trade, government,   japan, america, currency            | economic, currency, trade, peace, chinas, states, countries,   standard, america, world               |
| English      | 2         | Public health and war relief | Public health and war relief                                                    | 0.146          | public, control, problem, population, agricultural, hospital,   disease, council, people, country   | agricultural, disease, control, support, problem, treatment,   council, diseases, population, average |
<!-- #endregion -->

These topical differences translated in differences in the network of actors involved. It is important to notice first that the networks of actors, especially persons, are highly fragmented during this final period. Such fragmentation reflects disruptions in Rotary activities, discontinuation in press coverage during the war, and a high degree of personnel turnover after the war. However, it is still possible to identify persons and organisations that are more central than others.


#### Persons

<!-- #region citation-manager={"citations": {"": []}} -->
Rotary leaders were more prominent in the foreign press than they were in the Chinese press, and the most central persons differed. The foreign press centred on the two wartime district governors Kuang Fuzhuo and Yan Deqing (1878-1942). Railway engineer Yan Deqing 顏德慶 was a charter member and past president of the Peiping (Beijing) Rotary Club, of which he was a member from 1922 to 1929. In 1931, he established the Nanjing Rotary Club and became its first president. During the war, Yan took refuge in Shanghai, where he founded the “outport tiffin club” for refugee Rotarians (<cite data-cite="626961/4YPDTCZE"></cite>, p.251) and succeeded to Kuang Fuzhuo as district governor, when the latter died in December 1938 (1416767152). Yan helped to bridge topics related to war relief, specifically the refugee camp set up in cooperation with the Salvation Army, and topics related to Rotary organization during the war. Compared to his high degree centrality, S. Wolfe, an American citizen, president of the Rotary Club of Shanghai during the war, presented a lower betweenness centrality. Although he participated in numerous meetings and social events, he did not demonstrate the same brokering potential as Kuang Fuzhuo and Yan Deqing. By contrast, *Shenbao* focused on local members and post-war club presidents, such as Ma Boyue 馬伯樂, the officer in charge of the toy collection campaign, and Tan Wenxie 譚偉學, manager of the Shanghai Telephone Company (Shanghai dianhua gongsi 上海電話公司), president of the Shanghai Rotary Club and successor to Wang Zhengting (who remained central in *Shenbao*) as the new governor in charge of reorganizing the district after the war.
<!-- #endregion -->

The non-Rotarians mentioned in the two presses also differed. The *Shenbao* placed a stronger emphasis on social workers involved in war relief, such as Ma Ruishan 馬瑞山 (which is likely to be the Chinese transliteration of Brigadier Morris in the English-language press), chief of the Salvation Army in charge of managing the “beggar camp”. Furthermore, the Chinese press focused on transnational or translocal actors, such as the leaders of two Chinese delegations from Burma, Yu Balun 宇巴倫 and Zeng Yangfu 曾養甫, who visited Kunming (the terminal of the Burma Road) and Chongqing (which hosted the Nationalist government in exile) in December 1939 (SPSP193912150301) and September 1941 (SPSP194109050601, SPSP194109060601), respectively. Zeng Yangfu 曾養甫, the chief of the second delegation, emphasized the long-term strategic importance of the Burma-Kunming Road, not only to support the war effort but also to help economic reconstruction after the war. As a sign of their political significance, they were welcomed by prominent political leaders including Premier Kong Xiangxi, Minister of Foreign Affairs Wang Zhengting, Guomindang high-ranking officials, and university presidents (SPSP193912150301). As these events were not covered in the foreign press, we can hypothesize that foreign reporters were not invited to participate in these meetings restricted to Chinese officials, business elites and Chinese newspapers. The foreign press instead focused on American officials who participated in Shanghai-based social events, such as the Foreign Trade Week and the US Maritime Day held in May 1940 to commemorate the ship “China Queen” (Zhongguo huanghou 中國皇后)'s inaugural voyage from New York to Guangdong in 1785 (SPSP194005200704). The key actors associated with these topics were American officials Horace Smith and Julean Arnold during the war, and John Cabot (1901-1981), the US Consul-General in Shanghai after the war. Horace Smith, who was head of the commercial department of the Consulate General in Shanghai, spoke before the Rotary Club on the subject of reciprocal trade agreements in 1939 (1371507091), while Julean Arnold delivered a talk on the situation in China after the Japanese invasion. He was also the subject of an obituary at the time of his death in New York City in 1946 (1371513579). US consul John Cabot gave a talk before the Rotary Club in 1948 to dispel misconceptions regarding the US policy in Asia and to appease fears that the US were neglecting China while helping to rebuild Japan (1371519387, 1371519097, 1419908902).

<!-- #region jdh={"object": {"source": ["Most central persons in the two-mode networks of persons and documents during the third period (1938-1949), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-24", "anchor-table-24"] -->
| **Name** | **Pinyin**     | **Degree** | **Betweenness** |
|----------|----------------|------------|-----------------|
| 馬伯樂   | Ma Boyue       | 7          | 0.8181818182    |
| 宇巴倫   | Yu Balun       | 3          | 0.7142857143    |
| 王正廷   | Wang Zhengting | 3          | 0.4333333333    |
| 馬瑞山   | Ma Ruishan     | 3          | 0.7             |
| 司密斯   | Si Misi        | 2          | 0.5714285714    |
| 明思德   | Ming Side      | 2          | 0.3042328042    |
| 曾養甫   | Zeng Yangfu    | 2          | 0.6666666667    |
| 譚偉學   | Tan Weixue     | 2          | 0.1             |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central persons in the two-mode networks of persons and documents in the ProQuest corpus during the third period (1938-1949), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-25", "anchor-table-25"] -->
| **Name**        | **Degree** | **Betweenness** | **Name**         | **Degree** | **Betweenness** |
|-----------------|------------|-----------------|------------------|------------|-----------------|
| Chiang Kai-Shek | 4          | 0.5970302099    | Morris           | 2          | 0.3695788812    |
| Fong Sec        | 4          | 0.5126754662    | Ho               | 2          | 0.3614977103    |
| Wolfe           | 4          | 0.184041184     | Soong            | 2          | 0.1630824373    |
| John Cabot      | 3          | 0.684729064     | Kann             | 2          | 0.1630824373    |
| Horace Smith    | 3          | 0.6684491979    | Pan              | 2          | 0.15            |
| Julean Arnold   | 3          | 0.0531561462    | Francis Pan      | 2          | 0.15            |
| Huang           | 3          | 0.0381311544    | Juvenalius       | 2          | 0.1298374787    |
| Hitler          | 2          | 0.6666666667    | Chen (Physician) | 2          | 0.1095447607    |
| Mussolini       | 2          | 0.5714285714    | Young            | 2          | 0.052796983     |
| Yen Te-Ching    | 2          | 0.4947472389    | Poate            | 2          | 0.0305288677    |
| Carlos Romulo   | 2          | 0.4395604396    | Chang            | 2          | 0.0305288677    |
| Yang            | 2          | 0.3850228967    | Wu               | 2          | 0.0153841549    |
<!-- #endregion -->

#### Organizations


Reflecting its focus on war relief and social welfare, the *Shenbao* highlighted the role of institutions such as the Salvation Army and the Shanghai Municipal Council, which teamed up to solve the “beggar” problem, and the Rotary Toy Hospital (Wanju yiyuan 玩具醫院) aimed at entertaining underprivileged children. Founded in London in 1865, the Salvation Army was (and still is) a Protestant Christian church and an international charitable organization which aimed to bring salvation to the poor, destitute, and hungry by meeting both their “physical and spiritual needs." It was introduced in China in 1915 and remained active in the country until 1952. Like in the previous decades, the SMC was also mentioned in lectures dealing with various topics related to social welfare and urban management, including child protection (SPSP194110101113), police (SPSP194007091105), and municipal finances (SPSP194003150907). The next most central institutions during the war were related to China-Burma relations, which were of strategic importance for conveying war supplies through the Burma Road until the Japanese occupation of Burma in 1942. Such transnational institutions included the China-Burma Cultural Association (Zhongmian wenhua xiehui 中緬文化協會) established during the first delegation to Chongqing in December 1939 (SPSP193912160601), and the China-Burma delegation (Zhongguo fangmiantuan 中國訪緬團) led by Zeng Yangfu 曾養甫 in September 1941 (SPSP194109050601, SPSP194109060601).


Due to its topical emphasis on macro-level geopolitics, the foreign press centred on high-level institutions (national governments, League of Nations). Chambers of commerce also played a pivotal role due to the focus on Sino-US economic relations and the intense press coverage of the Foreign Trade Week in January 1940. More intriguing is the high betweenness centrality of St. John’s University. While the centrality of educational institutions is not a new phenomenon, St John’s assumed novel roles during the war. Acting as a sort of neutral zone in occupied Shanghai, its campus continued to serve as a meeting ground for various social events, including the Rotary Garden Party and interschool sports competition sponsored by the Rotary Club (1371782523, 1371507091). St John’s university is also mentioned in connection with former students who became members of the Rotary Club, such as Huang Yankai 黄岩凯 (Huang Yen-kai), a Guangdong-born journalist and consular official, who studied journalism and political science at St John’s (1922-1924) and became president of the Rotary Club of Penang in Malaysia (1371497748), and Cheng Siliang 沈嗣良 (William Sung), who was elected president of the Shanghai Rotary Club in 1941 and 1945, and served as acting district governor in 1941 (1371511710). The Sokol Club was another institution which was specific to the foreign press, reflecting its topical emphasis on the Russian community (1371437477, 1418909436). Although little is known on this club, it seemed to be central to the life of the Russians in Shanghai.  

<!-- #region jdh={"object": {"source": ["Most central organizations in the two-mode networks of persons and documents in the Shenbao corpus during the third period (1938-1949), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-26", "anchor-table-26"] -->
| **Name**       | **Pinyin**              | **Transliteration**              | **Degree** | **Betweenness**       |
|----------------|-------------------------|----------------------------------|------------|-----------------------|
| 扶輪社         | Fulunshe                | Rotary Club                      | 100        | 0.8653656053          |
| 上海扶輪社     | Shanghai fulunshe       | Shanghai Rotary Club             | 29         | 0.3021206355          |
| 工部局         | Gongbuju                | Shanghai Municipal Council       | 12         | 0.1857299024          |
| 救世軍         | Jiushijun               | Salvation Army                   | 11         | 0.0240046608          |
| 扶輪社玩具醫院 | Fulunshe wanju yiyuan   | Rotary Club Toy Hospital         | 7          | 0.070343725           |
| 國際扶輪社     | Guoji fulunshe          | Rotary International             | 7          | 0.0636480063          |
| 美僑總會       | Meiqiao zonghui         | American Overseas Association    | 3          | 1.2033384045451812E-4 |
| 社會局         | Shehuiju                | Bureau of Social Affairs         | 2          | 6.704313968180296E-4  |
| 中緬文化協會   | Zhongmian wenhua xiehui | China-Burma Cultural Association | 2          | 4.125731672726335E-4  |
| 新光油漆公司   | Xinguang youqi gongsi   | New Light Paint Company          | 2          | 2.5785822954539595E-5 |
| 中國訪緬團     | Zhongguo fangmian tuan  | Chinese Burma Delegation         | 2          | 1.2892911477269798E-5 |
| 行政院         | Hangzhengyuan           | Executive Yuan                   | 2          | 0.0353265774          |
| 馬迪汽車公司   | Madiqiche gongsi        | Mark Moody (automobile company)  | 2          | 0.0142853459          |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most central organizations in the two-mode networks of persons and documents in the ProQuest corpus during the third period (1938-1949), using degree centrality and betweenness centrality as metrics."], "type": "table"}} tags=["hermeneutics", "table-27", "anchor-table-27"] -->
| **Name**                      | **Degree** | **Betweenness** | **Name**                     | **Degree** | **Betweenness** |
|-------------------------------|------------|-----------------|------------------------------|------------|-----------------|
| Rotary Club                   | 51         | 0.69746943      | Embassy                      | 3          | 0.00938351      |
| Shanghai Rotary Club          | 25         | 0.21586752      | Navy                         | 3          | 0.00567443      |
| Government                    | 9          | 0.05260806      | North-China Daily News       | 3          | 0.00526784      |
| China Press                   | 6          | 0.02974823      | Customs                      | 3          | 0.00466082      |
| United Press                  | 6          | 0.01905889      | American Chamber of Commerce | 3          | 0.00366428      |
| Rotary International          | 5          | 0.01225567      | American Red Cross           | 2          | 8.6115E-4       |
| Salvation Army                | 5          | 0.01121386      | Central Government           | 2          | 7.68E-5         |
| National Government           | 5          | 0.00695915      | Commonwealth                 | 2          | 5.514E-5        |
| St John's University          | 4          | 0.08641229      | Shanghai Municipal Police    | 2          | 4.7129E-4       |
| League of Nations             | 4          | 0.03583651      | Hankow Rotary Club           | 2          | 4.443E-5        |
| Ministry of Communications    | 4          | 0.03307317      | Shanghai Municipal Council   | 2          | 4.126E-4        |
| Army                          | 4          | 0.01055993      | Foreign office               | 2          | 3.0952E-4       |
| Chamber of Commerce           | 4          | 0.00305703      | American Government          | 2          | 3.0638E-4       |
| Anti-Venereal League of China | 3          | 3.2944E-4       | Hongkong Government          | 2          | 2.5444E-4       |
| Kuomintang                    | 3          | 0.03791533      | British Government           | 2          | 2.3736E-4       |
| Domei                         | 3          | 0.02032924      | Chinese Medical Association  | 2          | 1.2659E-4       |
| China Weekly Review           | 3          | 0.02021597      | Lord Mayor's Fund            | 2          | 1.0903E-4       |
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} -->
## Part III. Mapping the Public Sphere: Rotary Geographic Imagination(s)
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["hermeneutics"] -->
This section seeks to empirically delineate the transnational contours of the public sphere in Republican Shanghai by mapping the geographic imaginations of Rotary members and newspaper readers. The primary step is to identify and standardize the names of locations and geopolitical entities (GPE) mentioned in the two corpora under study using named entity recognition. After standardizing place names, which involves homogenizing variants and finding contemporary names for old place names, R packages were employed to geolocate the countries and cities most frequently mentioned in the corpora. For mapping historical Chinese cities, the [Modern China Geospatial Database (MCGD)](https://analytics.huma-num.fr/enpchina/MCGD_interface/), a reference geospatial database for modern China created by the ENP-China project, was utilized. To compare the geographical imaginations of each language community and study how the geographic landscape evolved over time, a map was designed for each period and each corpus. It's crucial to note that the maps only represent places to which geographical coordinates can be associated. Metaphorical place names such as "Orient" or "Far East" are not included in the representations. To address this gap, the maps are supplemented with a series of tables listing all the most frequent place names in the two corpora, regardless of their "mappability". The complete code for extracting, standardizing, and mapping place names is accessible in the GitHub "script" folder. The subsequent narrative layer provides an in-depth interpretation of the resulting geographies.
<!-- #endregion -->

```R jdh={"object": {"source": ["Most frequent countries mentioned in the *Shenbao* (above) and ProQuest (below) Rotary corpus. The color gradient represents the mean frequency of mentions over all periods. Interactive maps are accessible on the Github repository."], "type": "image"}} tags=["figure-16"]
library("IRdisplay")
display_jpg(file="./media/Fig16a.JPG")
display_jpg(file="./media/Fig16b.JPG")
```

```R jdh={"object": {"source": ["Most frequent cities mentioned in the *Shenbao* (above) and ProQuest (below) Rotary corpus. The size of the circles is proportional to the mean frequency of mentions over all periods. Interactive maps are accessible on the Github repository."], "type": "image"}} tags=["figure-17"]
library("IRdisplay")
display_jpg(file="./media/Fig17a.JPG")
display_jpg(file="./media/Fig17b.JPG")
```

### Pacific and Colonial Focuses (1919-1929)


During the post-WWI phase, the two corpora are centered on China and the Pacific area, specifically the three main bordering countries controlling the Pacific area: China, the United States (including Hawaii), and Japan. Japan is primarily mentioned in connection with the Rotary Club Convention organized in Tokyo in October 1928 and as the subject of several lectures. The English corpus exhibits a more British-centered focus, with a stronger emphasis on the United Kingdom (Britain, Great Britain, England, Scotland) and British colonies, including Hong Kong, Canada, Australia, and India. At a finer level, English periodicals mention several cities in the United Kingdom, such as London, Liverpool, Glasgow, and Manchester. This coverage reflects the focus of the British *North-China Herald*, which included a specific "Scottish Letter," and the predominantly British readership's interest in events in their homeland. In contrast, *Shenbao* highlights less common world regions, such as South America, mentioned in reference to US Senator Bingham's trip and in a talk on Kodak business on this subcontinent. Despite the massive waves of Chinese migration to South America since the 19th century, the reporter emphasizes that this region of the world may not be well-known to Chinese readers. The *Shenbao* seems to take pride in being among the few newspapers in China to cover this region.


In addition to Shanghai, which dominated as the centre of the press industry and the birthplace of the Rotary Club in China, the main Chinese cities mentioned during this period included the former and current national capitals Beijing and Nanjing. Beijing, Nanjing, and Tianjin are also mentioned because Rotary Clubs or sister organizations like Y’s Men Clubs were founded in these cities. Additionally, they were "passage obliges" for the many foreign personalities who visited China during this period, such as the world-famous Protestant pastor Eddy Sherwood (1871-1963) in 1922 (SPSP192211171601) or US Senator Hiram Bingham (1875-1956) in 1927 (SPSP192708051409). Guangzhou and the Guangdong province were mentioned exclusively in connection with the smallpox prevention campaign sponsored by the Rotary Club in 1925. While non-Chinese cities in *Shenbao* were principally located in Asia and the Pacific area (Tokyo, Honolulu), the geographic scope in the English press was much wider, spanning France, Russia, Germany, Africa, and including foreign cities like New York, Paris, Washington, San Francisco, Boston, Chicago, where various international conferences and exhibitions took place in which Chinese delegates participated. The range of cities and provinces outside Shanghai is also wider in the English press, including mostly cities with a strong foreign or missionary presence, like Hankou, Shandong, and Harbin.

<!-- #region jdh={"object": {"source": ["Most frequent locations and geopolitical entities (GPE) mentioned in the Shenbao Rotary corpus during the first period (1919-1929)."], "type": "table"}} tags=["hermeneutics", "table-28", "anchor-table-28"] -->
| **Location**           | **Count** | **Location**              | **Count** |
|------------------------|-----------|---------------------------|-----------|
| 上海 (Shanghai)        | 35        | 太平洋 (Pacific)          | 2         |
| 美國 (United States)   | 12        | 廣東 (Guangdong)          | 2         |
| 中國 (China)           | 10        | 意大利 (Italy)            | 2         |
| 北京 (Beijing)         | 6         | 東京 (Tokyo)              | 2         |
| 日本 (Japan)           | 5         | 檀香山 (Honolulu)         | 2         |
| 南京 (Nanjing)         | 4         | 歐美 (Europe and America) | 2         |
| 南美洲 (South America) | 2         | 浦東 (Pudong)             | 2         |
| 天津 (Tianjin)         | 2         | 遠東 (Far East)           | 2         |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most frequent locations and geopolitical entities (GPE) mentioned in the ProQuest (English) Rotary corpus during the first period (1919-1929)."], "type": "table"}} tags=["hermeneutics", "table-29", "anchor-table-29"] -->
| **Location**  | **Count** | **Location**  | **Count** | **Location**  | **Count** |
|---------------|-----------|---------------|-----------|---------------|-----------|
| China         | 114       | Canada        | 11        | Africa        | 6         |
| Shanghai      | 99        | France        | 11        | Boston        | 6         |
| United States | 45        | Great Britain | 11        | Chicago       | 6         |
| America       | 44        | North China   | 11        | Germany       | 6         |
| Peking        | 37        | West          | 11        | Italy         | 6         |
| Japan         | 35        | Hankow        | 10        | Scotland      | 6         |
| Europe        | 23        | India         | 10        | Shantung      | 6         |
| London        | 21        | Philippines   | 10        | Glasgow       | 5         |
| England       | 20        | Russia        | 10        | Harbin        | 5         |
| Hongkong      | 19        | Manchuria     | 9         | Hawaii        | 5         |
| New York      | 19        | Pacific       | 9         | Honolulu      | 5         |
| Tientsin      | 19        | Tokyo         | 9         | Kobe          | 5         |
| Nanking       | 17        | Australia     | 8         | Manchester    | 5         |
| Manila        | 16        | Britain       | 8         | Mukden        | 5         |
| Washington    | 15        | East          | 8         | New York City | 5         |
| Paris         | 14        | Singapore     | 8         | North         | 5         |
| Asia          | 13        | Liverpool     | 7         | Rome          | 5         |
| Canton        | 12        | Orient        | 7         | Shanghai's    | 5         |
| Far East      | 12        | San Francisco | 7         | Yokohama      | 5         |
<!-- #endregion -->

### Expanding Horizons (1930-1937)


The second period is characterized by a broadening of geographic horizons in the two corpora, particularly in *Shenbao*. While the Pacific area remained prominent during this period, *Shenbao* began to include new locations, such as British colonies (Hong Kong, India) and European countries, such as France and Portugal. In the English corpora, a new focus on Germany and Italy reflected the growing concern with the spread of fascism in Europe. Switzerland and Geneva were mentioned in connection to the League of Nations and its mission to preserve international peace. It is interesting to note that while expressions like "Far East" (*Yuandong* 遠東) and "Orient" (*Dongfang* 東方) were losing momentum in *Shenbao*, they persisted in the English press, which concurrently employed the term “Asia”. The equivalent term in Chinese (*Yazhou* 亞洲) was utterly absent from *Shenbao* during this period, suggesting that the political tensions among Asian countries, especially China-Japan, prevented the emergence of an Asian sentiment among *Shenbao* reporters and editors.


Although geographical boundaries expanded in the two corpora, the English press maintained a wider coverage than *Shenbao*, including countries like Russia and New Zealand, and foreign cities like Geneva (headquarters of the League of Nations), Berlin, Rome, and Osaka. In China proper, the foreign press featured a wide range of cities including Xiamen, Fuzhou, Suzhou, Wuhu (current Wuhan), in which Rotary Clubs were founded during the 1930s. In *Shenbao*, emerging Chinese cities like Hangzhou and Qingdao, where Rotary Clubs were established during the same decade, received greater attention. As indicated earlier, Hangzhou became a key touristic destination during this period, and the Qingdao mayor demonstrated a keen interest in the local Rotary Club, hoping to gain local elites’ support for his plan of developing his city’s prosperity. Having lost capital status as the national capital, Beijing was much less mentioned than Nanjing in both presses. There was also the emergence of broader, less specific toponyms like North China and Manchuria, reflecting the new focus on this region after the Japanese invasion of September 1931, and the Northwest, in connection to large-scale infrastructural projects in this region. On the opposite end, more specific locations, including street names in Shanghai, gained prominence during this period, indicating meeting places or referring to philanthropic endeavours, such as hospitals or schools sponsored by the Shanghai Rotary Club.


<!-- #region jdh={"object": {"source": ["Most frequent locations and geopolitical entities (GPE) mentioned in the Shenbao Rotary corpus during the second period (1930-1937)."], "type": "table"}} tags=["hermeneutics", "table-30", "anchor-table-30"] -->
| **Location**              | **Count** | **Location**                          | **Count** |
|---------------------------|-----------|---------------------------------------|-----------|
| 中國 (China)              | 62        | 中西 (China-West)                     | 4         |
| 上海 (Shanghai)           | 48        | 北平 (Beiping)                        | 4         |
| 日本 (Japan)              | 35        | 青島 (Qingdao)                        | 4         |
| 美國 (United States)      | 24        | 駐美 (Stationed in the United States) | 4         |
| 英國 (United Kingdom)     | 17        | 華北 (North China)                    | 4         |
| 西北 (Northwest)          | 15        | 桐廬 (Tonglu)                         | 4         |
| 杭州 (Hangzhou)           | 10        | 抵菲 (Arrive in the Philippines)      | 4         |
| 香港 (Hong Kong)          | 10        | 太平洋 (Pacific)                      | 4         |
| 抵滬 (Arrive in Shanghai) | 10        | 葡萄牙 (Portugal)                     | 3         |
| 歐洲 (Europe)             | 10        | 返滬 (Return to Shanghai)             | 3         |
| 遠東 (Far East)           | 9         | 離杭 (Leave Hangzhou)                 | 3         |
| 上海市 (Shanghai City)    | 8         | 澳大利亞 (Australia)                  | 3         |
| 來滬 (Arrive in Shanghai) | 8         | 靜安寺路 (Jing'an Temple Road)        | 3         |
| 南京路 (Nanjing Road)     | 6         | 法國 (France)                         | 3         |
| 南京 (Nanjing)            | 6         | 南京 (Nanjing)                        | 3         |
| 印度 (India)              | 6         | 漢路 (Han Road)                       | 3         |
| 倫敦 (London)             | 6         | 石家莊 (Shijiazhuang)                 | 3         |
| 菲律賓 (Philippines)      | 6         | 平綏路 (Ping Sui Road)                | 3         |
| 太原 (Taiyuan)            | 6         | 綏遠 (Suiyuan)                        | 3         |
| 大同 (Datong)             | 6         | 經蔭縣 (Through Yin County)           | 3         |
| 包頭 (Baotou)             | 6         | 黃河 (Yellow River)                   | 3         |
| 靑島 (Qingdao)            | 6         | 夏蘭州西安 (Xialan Prefecture, Xi'an) | 3         |
| 德國 (Germany)            | 5         | 廣東 (Guangdong)                      | 3         |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most frequent locations and geopolitical entities (GPE) mentioned in the ProQuest (English) Rotary corpus during the second period (1930-1937)."], "type": "table"}} tags=["hermeneutics", "table-31", "anchor-table-31"] -->
| **Location**                  | **Count** | **Location**  | **Count** |
|-------------------------------|-----------|---------------|-----------|
| China                         | 377       | Asia          | 20        |
| Shanghai                      | 322       | California    | 20        |
| United States/America         | 230       | Manchuria     | 19        |
| Japan                         | 129       | Pacific       | 19        |
| England/Britain/Great Britain | 119       | North China   | 18        |
| Nanking                       | 105       | Singapore     | 18        |
| Europe                        | 68        | Amoy          | 16        |
| Peiping/Peking                | 56        | Foochow       | 16        |
| Far East                      | 55        | Kiangsu       | 16        |
| London                        | 53        | Orient        | 16        |
| Germany                       | 48        | Paris         | 16        |
| Russia                        | 43        | Shanghai      | 16        |
| Hong Kong                     | 38        | Geneva        | 15        |
| Manila                        | 37        | Soochow       | 15        |
| Canton                        | 35        | Tsingtao      | 14        |
| Tokyo                         | 33        | Berlin        | 13        |
| Australia                     | 32        | New Zealand   | 13        |
| New York                      | 29        | Rome          | 12        |
| Chicago                       | 28        | San Francisco | 12        |
| France                        | 28        | Chekiang      | 11        |
| India                         | 28        | Moscow        | 11        |
| Philippines                   | 28        | South China   | 11        |
| Tientsin                      | 28        | Wuhu          | 11        |
| Hankow                        | 27        | Honan         | 10        |
| Italy                         | 27        | Hsiakwan      | 10        |
| Washington                    | 27        | Osaka         | 10        |
| Hangchow                      | 26        | Shantung      | 10        |
<!-- #endregion -->

### Covering War Fronts (1938-1949)


The third period witnessed a clear shift towards Western China (Sichuan, Chongqing, Kunming, Chengdu), the only area preserved from Japanese occupation after 1937. After the Nationalist government was forced to relocate its capital from Nanjing to Chongqing, *Shenbao* focused on Chongqing and the China-Burma frontier (Myanmar, China-Myanmar, Yangon), a strategic route in the war effort and post-war reconstruction. Furthermore, the Chinese newspaper paid greater attention to countries that were pivotal in the war effort, including India (where British troops were stationed), Australia (which had become a vital supplier of food and manufactured goods in South Asia during the war), and Malaysia (where overseas Chinese had established a “patriotic fund” to support the war effort in their home country). While China and the United States remained prominent, Japan as a country was surprisingly underrepresented. This apparent omission, in fact, signalled that the frontier had shifted, as Japan had become a dividing line within the Chinese territory itself. Besides Shanghai and Chongqing, *Shenbao* mentioned a few places in occupied China, including Hankou, Guangzhou, and Hangzhou, and the Suzhou River.


By contrast, the geographical landscape in the English press was barely altered by the outbreak of the war and the Japanese occupation. This may reflect the fact that many foreign papers ceased to appear or fell under Japanese control after the Japanese occupation of Shanghai. China, Japan, and the United States remained the most prominent countries. For the first time, however, Japan became more important than the United States, in sharp contrast with the evolution observed in the Chinese press. The English press was clearly more focused on the European front (Europe, London, Russia, England, Germany, Austria, Italy), leaving little room for Chongqing and the Burma front. The focus was on Japanese-occupied China (Manchukuo, Harbin) and the South Pacific area of resistance, including Hong Kong, Philippines/Manila, and Siam.

<!-- #region jdh={"object": {"source": ["Most frequent locations and geopolitical entities (GPE) mentioned in the Shenbao Rotary corpus during the third period (1938-1949)."], "type": "table"}} tags=["hermeneutics", "table-32", "anchor-table-32"] -->
| **Location**              | **Count** | **Location**                   | **Count** |
|---------------------------|-----------|--------------------------------|-----------|
| 中國 (China)              | 43        | 駐滬 (Stationed in Shanghai)   | 4         |
| 美國 (United States)      | 23        | 漢口 (Hankou)                  | 4         |
| 上海 (Shanghai)           | 21        | 仰光 (Yangon)                  | 4         |
| 香港 (Hong Kong)          | 18        | 中緬 (China-Myanmar)           | 4         |
| 重慶 (Chongqing)          | 12        | 靜安寺路 (Jing'an Temple Road) | 3         |
| 昆明 (Kunming)            | 10        | 廣州 (Guangzhou)               | 3         |
| 緬甸 (Myanmar)            | 10        | 遠東 (Far East)                | 3         |
| 日本 (Japan)              | 8         | 中西 (China-West)              | 3         |
| 英國 (United Kingdom)     | 7         | 加拿大 (Canada)                | 3         |
| 馬來 (Malaysia)           | 6         | 馬尼 (Manila)                  | 3         |
| 成都 (Chengdu)            | 6         | 大陸 (Mainland)                | 3         |
| 南京 (Nanjing)            | 5         | 蘇州河 (Suzhou River)          | 3         |
| 來滬 (Arrive in Shanghai) | 4         | 根特開省 (Ghent Province)      | 3         |
| 澳洲 (Australia)          | 4         | 杭州 (Hangzhou)                | 3         |
| 印度 (India)              | 4         | 緬訪 (Visit to Myanmar)        | 3         |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Most frequent locations and geopolitical entities (GPE) mentioned in the ProQuest (English) Rotary corpus during the third period (1938-1949)."], "type": "table"}} tags=["hermeneutics", "table-33", "anchor-table-33"] -->
| **Location**  | **Count** | **Location** | **Count** | **Location**  | **Count** |
|---------------|-----------|--------------|-----------|---------------|-----------|
| Shanghai      | 48        | Britain      | 5         | Africa        | 3         |
| China         | 46        | Canton       | 5         | Burma         | 3         |
| Japan         | 20        | Peking       | 5         | Chengdu       | 3         |
| America       | 22        | Philippines  | 5         | East          | 3         |
| United States | 19        | Singapore    | 5         | Far Eastern   | 3         |
| Hong Kong     | 14        | Australia    | 4         | France        | 3         |
| Far East      | 12        | Austria      | 4         | Hankou        | 3         |
| Europe        | 11        | Berlin       | 4         | Harbin        | 3         |
| London        | 9         | India        | 4         | Manchoukuo    | 3         |
| Russia        | 9         | Indo-China   | 4         | Manila        | 3         |
| Tokyo         | 9         | Italy        | 4         | North China   | 3         |
| Washington    | 8         | Malaya       | 4         | Pacific       | 3         |
| Chungking     | 6         | New York     | 4         | Peiping       | 3         |
| England       | 6         | Orient       | 4         | Rangoon       | 3         |
| Germany       | 6         | Paris        | 4         | San Francisco | 3         |
| Nanking       | 6         | Tsingtao     | 4         | Siam          | 3         |
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
In conclusion, this comparative, bilingual analysis of locations and geopolitical entities (GPE) over three decades highlights the persisting importance of nation-states, supporting the argument that the "transnational" did not mean the end of the national (<cite data-cite="626961/CDLF6DBW"></cite>, <cite data-cite="626961/8LDCAR4J"></cite>). Historically, the significance of country entities reflects the rise of international tensions and tedious efforts to maintain international cooperation during the interwar years. The list of countries is largely reflective of the major nationalities represented in Shanghai (<cite data-cite="626961/TPUGQE3W"></cite>), although horizons broadened in the 1930s and attention shifted to geopolitically sensitive areas as political tensions heightened and eventually led to WWII.
<!-- #endregion -->

As observed for actors, the geographic imaginations of the two corpora converged during the 1930s but diverged again during the war and post-war period. The Pacific area remains central in the two corpora. Differences in scope and focus occurred at the external and internal borders of this core region. During the first period, *Shenbao* showed an intriguing interest in South America, whereas the English press remained within the confines of the British Empire. A persisting difference between the two linguistic communities is the total omission of Africa on *Shenbao*’s world map, reflecting the lack of interest among Chinese readers as much as the lack of Chinese reporters on this continent, whereas Africa enjoyed a continuing presence in the foreign press, reflecting the extent of colonial empires.


Within the Chinese territory, the English press covered a wider territory compared to *Shenbao*, relying on missionary and business networks established since prior to the Opium wars, whereas Chinese journalists remained focused on major cities, especially the national capitals, and cities where Rotary Clubs and Y’s Men’s clubs were established. The horizons broadened during the 1930s following the extension of infrastructural projects around Hangzhou and in Northwest China. During the war, the gap widened both inside and outside China. Inside China, *Shenbao* followed the Nationalist government and focused on Chongqing and the Sichuan-Burma border, whereas the English press was more concerned by the situation in occupied China. Outside China, the English press focused on the European front, whereas *Shenbao* focused more on the South Pacific as a source of supply and support from overseas Chinese in the war effort.


## Part IV. Articulating the Public Sphere: Key Terms and Semantic Constellations


This final section constitutes an empirical investigation of the concepts associated with the transnational public sphere, specifically defined in the context of the Rotary Club in China during the Republican period. The key questions include: (1) What are the main senses of the term “public” (*gong* 公 in Chinese) and nation-based terms (*guo* 國 in Chinese) in the two corpora? (2) How did these concepts relate to the operating modes of the Rotary Club identified in the first section? (3) How did they evolve over time, in relation to the topical shifts and changes of actors identified in the second section? (4) How did these semantic shifts and constellations compare across the two language-based corpora?



### Methodology

<!-- #region tags=["hermeneutics"] -->
This conceptual analysis involves several pre-processing steps, including tokenization (word segmentation) and eliminating  Optical Character Recognition (OCR) noise in English. The nature of operations varies depending on the language. For brevity, these steps are detailed in the “script” folder on the GitHub repository.

Based on the cleaned, properly tokenized texts, my methodology followed several steps. First, I employed concordance, or Keyword In Context (KWIC), to identify terms containing the character *guo* 國 (commonly translated as nation or country) and *gong* 公 (public) in Chinese. In the English press, I looked for the most frequent bigrams (ie, pairs of adjacent words) associated with the terms “international” and “public.” I used different metrics to identify the most frequent terms or bigrams in each corpus. In addition to simple frequencies, I used Term Frequency-Inverse Document Frequency (TF-IDF) to examine how the use of these terms evolved over time, based on the periodization defined in the previous sections. TF-IDF is a numerical statistic reflecting the importance of a term in a document relative to a collection of documents (corpus). It is commonly used in information retrieval and text mining to assess the significance of terms within a document or a set of documents.

Finally, I searched for the most frequent collocates of these key terms to explore the broader semantic contexts in which they occurred. Collocates are words that often appear together with a given term. I compared two primary metrics for identifying collocates: pairwise count and log-likelihood. Pairwise count refers to the number of times two specific items or elements occur together in pairs within a given context. This concept is commonly used when analyzing co-occurrence patterns in textual data, such as counting the occurrences of word pairs or term pairs within a set of documents. Log-likelihood is a more sophisticated method, assessing the likelihood of an observed set of data given a particular hypothesis or model. In the context of co-occurrence analysis in linguistics or text mining, log-likelihood is used to evaluate the significance of the association between two words (or terms) by comparing their observed co-occurrence frequency with the expected frequency under a specific statistical model.

The results of this semantic exploration are presented in the following narrative layer.

<!-- #endregion -->

### Mapping the Transnational


#### The Chinese Press: Multinational Encounters and Transpacific Exchanges


[Table 34](#anchor-table-34) lists the most frequent 國 *guo*-based terms in the *Shenbao* Rotary corpus using simple frequency count.

<!-- #region jdh={"object": {"source": ["Most frequent terms based on \u570b (guo) in the Shenbao Rotary corpus. The highlighted terms are the most akin to the concept of the 'transnational'."], "type": "table"}} tags=["hermeneutics", "table-34", "anchor-table-34"] -->
| **Chinese** | **Pinyin** | **Translation**                       | **Count** | **Chinese** | **Pinyin** | **Translation**                  | **Count** |
|-------------|------------|---------------------------------------|-----------|-------------|------------|----------------------------------|-----------|
| 中國        | Zhongguo   | China                                 | 254       | 德國        | Deguo      | Germany                          | 13        |
| 美國        | Meiguo     | United States                         | 119       | 國代        | Guodai     | National representatives         | 13        |
| **國際**    | **Guoji**  | **International**                     | 111       | 國內        | Guonei     | Domestic (within the country)    | 11        |
| **各國**    | **Geguo**  | **Various countries (multinational)** | 54        | 吾國        | Wuguo      | Our country                      | 8         |
| 英國        | Yingguo    | United Kingdom                        | 41        | 國内        | Guonei     | Domestic (within the country)    | 8         |
| 國人        | Guoren     | National(s) (people of the country)   | 28        | 國外        | Guowai     | Abroad (outside the country)     | 8         |
| 我國        | Woguo      | My country                            | 27        | 國徽        | Guohui     | National emblem                  | 8         |
| 全國        | Quanguo    | Nationwide                            | 26        | 國體        | Guoti      | National body                    | 8         |
| **萬國**    | **Wanguo** | **All nations**                       | 25        | **進國**    | **Jinguo** | **Enter the country**            | 8         |
| 國家        | Guojia     | Home country                          | 15        | **國外**    | **Guowai** | **Abroad (outside the country)** | 8         |
| 外國        | Waiguo     | Foreign country                       | 15        | **回國**    | **Huiguo** | **Return to the country**        | 7         |
| 國民        | Guomin     | National(s) (citizens of a country)   | 14        | 本國        | Benguo     | Home country                     | 7         |
| 法國        | Faguo      | France                                | 14        | **返國**    | **Fanguo** | **Return to the country**        | 7         |
| 國籍        | Guoji      | Nationality                           | 13        | 民國        | Minguo     | Republic of China                | 6         |
<!-- #endregion -->

*Shenbao* delineates five main conceptions of the transnational, illustrated as five distinct clusters or semantic constellations in [figure 18](#anchor-figure-18). These constellations exhibit a spectrum ranging from the national to the global and are partially interconnected. The most prominent cluster revolves around the term *guoji* (國際), commonly translated as international. This term predominantly denotes the activities of Rotary International (Guoji Fulunshe 國際扶輪社), focusing primarily on organizational aspects, including the election of presidents (*huizhang* 會長), establishment of local branches (*fenshe* 分社), hosting conferences (*huiyi* 會議), and conducting meetings (*canjia* 參加) in Western-style hotels (*fanguan* 飯館). This cluster also encompasses the names of Chinese cities where Rotary clubs were established, predominantly in southern China (Nanjing, Hankou, Suzhou).

```R jdh={"object": {"source": ["Network graph illustrating the most frequent collocates of \u570b-based terms in the *Shenbao* Rotary corpus. Only collocates with a weight exceeding 2, calculated using pairwise count per document, are displayed. The colour gradient reflects eigenvector centrality, with red nodes indicating higher centrality than yellow nodes. Node size corresponds to the frequency of each term in the corpus. For precise figures on weight and frequency, refer to the attached tables. Note: Eigenvector centrality is a measure of the influence of a node in a network, taking into account both the node's direct connections and the connections of its neighbours. Co-occurrence weights (pairwise count) were computed using tidytext and widyR, and the network visualizations were created using igraph, tidygraph, and ggraph."], "type": "image"}} tags=["figure-18", "anchor-figure-18"]
library("IRdisplay")
display_jpg(file="./media/Fig18.JPG")
```

The *guoji* constellation incorporates special programs sponsored by the Rotary Club, emphasizing economic development (*fazhan* 發展), construction (*jianshe* 建設), and public health (*weisheng* 衛生). It involves individuals who traverse borders, typically high-ranking officials of internal prominence, such as Wang Zhengting, who frequently traveled abroad (eventually returning to their home country, *huiguo* 回國), often making public appearances with their spouses (expressed through the term *furen* 夫人, couple). The *guoji* cluster exhibits direct connections to other clusters, exemplified by *geguo* 各國 (translatable as multinational), or through intermediary terms such as China (Zhongguo 中國), bridging  *guoji*  with *guojia*  國家 (home country). Additionally, the term "meeting" (*canjia* 參加) serves as a link between *guoji* and *quanguo* 全國 (nationwide or throughout the country).


The second-largest cluster, directly linked to the preceding one, encompasses the two principal dimensions of the transnational as defined in the introduction. A sub-cluster, centred around the term *geguo* 各國, pertains to the notion of uniting multiple nations within the same contact zone. In the *Shenbao* context, this contact zone primarily designates Shanghai (referred to as *benshi* 本市 or “this city”). This sub-cluster revolves around specific events, such as *jucan* 聚餐 (translated as "tiffins") and *canjia* 參加 (meetings) organized by the Rotary Club and specific actions expressed through action verbs like *sheli* 設立 (establish) or *hezuo* 合作 (cooperate). These actions primarily focused on education and public safety (with terms like *anquan* 安全 and *tongzijun* 童子軍 Boy Scout), particularly during wartime (as indicated by *zhanshi* 戰事). The second dimension, centred on the term *quanguo* 全國 (literally nationwide or throughout the country), defines the transnational as subnational. It involves actions at the local level (such as *quyu* 區域 district) and engages non-state actors, including members of associations (like *sheyuan* 社員), particularly women's (婦女 *funü*) associations, organizations dedicated to social relief (*jiuji* 救濟), universities (*daxue* 大學), and overseas Chinese, specifically in America (*Meiqiao* 美僑). The term "meeting" (*canjia* 參加), which signifies the Rotary Club's key operational mode, serves as a link connecting its international and transnational dimensions.


The term "China" (Zhongguo) serves to connect Rotary International with concepts grounded in the national sphere. Three primary terms illustrate the persistence of the national framework despite the transnational orientation of the Rotary Club and its participants. The term *wanguo* 萬國 (all nations) predominantly emerged in relation to the annual tennis tournament (Shanghai wanguo wangqiu jinbiaosai 上海萬國網球錦標賽) and other sports competitions sponsored by the Rotary Club. This usage emphasized the national origin of participating teams, fostering international goodwill through friendly, sport-like competition. The term *guojia* 國家 (home country) conveys an emotional identification with the national territory and a sense of community (expressed as *wuren* 吾人), similar to *woguo* 我國 or *wuguo* 吾國 (my country). Both of these terms indicate the speaker's personal identification with their home country, often a delegate (*daibiao* 代表) or a committee member (*weiyuanhui* 委員會). The last cluster, centred on *waiguo* (foreign), is isolated from the rest of the network and is principally associated with the foreign presence in Shanghai and, to a lesser extent, with overseas issues (such as *guowai* 國外 or *haiwai* 海外).


This semantic analysis confirms that all terms presuppose a national framework. However, they relate to the nation in different ways and with varying degrees of dependence. In terms of importance, *wanguo* (all-nations) and *geguo* (multinational) are closer to nation-oriented terms like *guojia* or *woguo*, whereas *guoji* (international) and *quanguo* (nationwide) are more distant, and *waiguo* is semantically independent.


Furthermore, the contours of the transnational evolved over time, and this evolution can be empirically measured using Term Frequency-Inverse Document Frequency (TF-IDF) metrics ([figure 19](#anchor-figure-19)). In the immediate aftermath of World War I, multinational encounters dominated, notably exemplified by the national emblem ceremony held in December 1929 under the auspices of the Rotary Club (SPSP192912201501, SPSP192912201513). This ceremony represented a notable attempt to alter power dynamics in the semi-colonial context of Shanghai by prioritizing China during the flag presentation ceremony. The national emblems presented during the ceremony represented more than ten countries, portraying the Shanghai Rotary Club as an ideal venue for cultivating international friendship. The sequence of emblem presentations was organized based on the duration of each country's representation. As the host, China had the privilege of presenting its national emblem first, followed by emblems from countries such as the United Kingdom, the United States, France, Japan, Germany, Italy, and others. This arrangement effectively reversed power relations compared to the colonial order. The Rotary Club established a small, self-contained world in which the unequal power dynamics of the "real" world were virtually inverted.

```R jdh={"object": {"source": ["Most frequent two-character \u570b-based terms by decade in the *Shenbao* corpus, using TF-IDF as the metric."], "type": "image"}} tags=["figure-19", "anchor-figure-19"]
library("IRdisplay")
display_jpg(file="./media/Fig19.JPG")
```

During the 1930s, the decade witnessed a blend of multinational encounters, prominently showcased by the annual tennis tournament, and transnational exchanges, as evidenced by the use of the term *huiguo* (return to home country). The tennis competition aimed at promoting interest in sports and fostering international relations among participating countries (SPSP193008121208). The tournament was consistently won by Chinese tennis players during the first three years at least (SPSP193007291001, SPSP193107311036, SPSP193208151203). It was only in 1936 that a Western country (the United States) emerged victorious (SPSP193608271505). Similar to the national emblem ceremony organized in the previous decade, sports competition provided a space where China could seek revenge upon colonial countries with minimal consequences and risks for the aforementioned colonial nations. Transnational exchanges involved Chinese visitors abroad, such as the Chinese business delegation to the Philippines (Zhonghua shangye feilü binguan guangtuan 中華商業菲律賓觀光團) in 1935 (SPSP193502141101). Conversely, it also included foreign visitors to China, for instance, the president of the Rotary Club of Cleveland, who visited Shanghai and Hong Kong to study the automobile industry in 1931 (SPSP193102071618). Cross-border exchanges during this period involved the Chinese soldiers of the National Salvation Army (Zhongguo guomin jiuguo jun 中國國民救國軍) led by Wang Delin 王德林 (1875-1938), who, in 1933, returned with their families from Europe through Russia after being defeated by Japan in Manchuria (SPSP193303290901). Additionally, figures like Wang Zhengting, Chinese minister of foreign affairs and ambassador to the US, travelled across the Pacific in 1936 (SPSP193608210708, SPSP193610031001).


#### The Foreign Press: Preserving International Peace and the Cosmopolitan World of Treaty Ports


In the English-language press, the range of terms for expressing the transnational is more limited. Terms like “multinational” and “transnational” were anachronistic during the period under study. The semantic landscape, therefore, is constrained within a binary national/international framework. Table 35 lists the most frequent bigrams associated with “international” in the English-language Rotary corpus, using simple frequency ([table 35](#anchor-table-35)).

<!-- #region jdh={"object": {"source": ["Most frequent bigrams associated with 'international' in the English-language Rotary corpus, using simple frequency. The highlighted terms are the most akin to the concept of the 'transnational'."], "type": "table"}} tags=["hermeneutics", "table-35", "anchor-table-35"] -->
| **Bigram**                      | **Count** | **Bigram**                | **Count** |
|---------------------------------|-----------|---------------------------|-----------|
| rotary international            | 96        | international convention  | 7         |
| international club              | 49        | international association | 6         |
| international settlement        | 44        | international body        | 6         |
| **international relations**     | **29**    | international labour       | 6         |
| **international goodwill**      | **20**    | international treaties    | 6         |
| **international understanding** | **16**    | international camp        | 5         |
| **international peace**         | **13**    | international famine      | 5         |
| **international affairs**       | **11**    | international justice     | 5         |
| **international friendship**    | **11**    | international relief      | 5         |
| international trade             | 11        | international service     | 5         |
| international organization      | 8         | international tennis      | 5         |
<!-- #endregion -->

To gain a deeper understanding of the transnational aspects of the foreign press, I chose to analyse the collocates of the term "international." Based on log-likelihood, the most frequent collocates of the term "international" in order of importance are nations, world, peace, conference, countries, Japan, and propaganda. Except for "world," these terms predominantly uphold a national framework. Interestingly, the collocates of "national" are very similar, though the ranking differs: government, country, people, foreign. While both terms centre around the concept of "nation," the "international" constellation highlights an "external" perspective, whereas the "national" places emphasis on the "inside" point of view.


To further examine how the different terms relate to each other and identify the semantic clusters they form, I relied on two distinct methods: Principal Component Analysis (PCA), and network visualization. In this section, I used PCA to analyse and reduce the dimensionality of the term-collocate relationships. This method is particularly helpful for identifying associations between “international” and other terms in a more compact and interpretable representation, and for uncovering underlying patterns in how the term “international” and its collocates relate to each other. Drawing from Principal Component Analysis (PCA), two primary senses of the term "international" emerge in the foreign press, visualized in the following biplot ([figure 20](#anchor-figure-20)). This biplot results from the projection of a PCA based on the log-likelihood of the collocates. It distinctly separates two main groups of words, representing two fundamental senses of "international." On the left side, we encounter terms expressing the ideals of world peace and unity among nations, embodied through organizations like the League of Nations. The horizontal axis further distinguishes between ideals (above) and means of actions (below), such as pacts. On the right side of the plot, terms emphasize the pre-eminence of nation-states and group-based interests. Terms related to international conferences (conference, delegate, discussion) serve as mediators between these two senses. Interestingly, the Far East is more closely associated with the second sense (resilience of nations), whereas the Near East is more closely linked to the first sense (unity). Additionally, the horizontal axis further separates issues related to China-Japan relations (below) from those concerning other countries and events (above).

```R jdh={"object": {"source": ["Principal Component Analysis of the most frequent collocates of 'international' using log-likelihood as metrics."], "type": "image"}} tags=["figure-20", "anchor-figure-20"]
library("IRdisplay")
display_jpg(file="./media/Fig20.JPG")
```

Based on pairwise count, the most frequent collocates of "international" include world, conference (held), foreign, national, people, government, president, country, address, American, city, local, and united. These terms are quite similar to those associated with "national," with the ranking differing (e.g., "world" appears higher than "government" and "country"). Both terms maintain the nation as their core elements, but "international" emphasizes the "external" point of view. The network graph displays the most frequent collocates of "national" and "international" ([figure 21](#anchor-figure-21)). These two terms are closely connected, indicating that they frequently occurred together. Terms on the right side of the graph are more strongly associated with "national," while terms on the left are more linked to "international." The specific set of terms attached to each word reinforces the distinction between the inside/outside point of view. The graph also helps refine the two main senses of "international" identified through PCA. In the more common sense, it refers to external relations among nations or countries, expressed through terms like country, nations, national, people, and world. In a sense closer to the notion of "transnational," it relates to terms suggesting the crossing of national boundaries (mostly through business relations) and contact zones (city, local, hotel) facilitating the coming together of various nationalities. Terms like foreign, American, and Japanese pertain to both senses, though they are more likely associated with the "transnational" sense. On the contrary, terms like "life" and "public" are primarily associated with "national."

```R jdh={"object": {"source": ["Network graph showing the most frequent collocates of 'national' and 'international' in the English-language Rotary corpus. Only collocates with a weight exceeding 50, calculated using pairwise count per document, are displayed. The colour gradient reflects eigenvector centrality. Node size corresponds to the frequency of each term in the corpus. For precise figures on weight and frequency, refer to the attached tables."], "type": "image"}} tags=["figure-21", "anchor-figure-21"]
library("IRdisplay")
display_jpg(file="./media/Fig21.JPG")
```

Like in *Shenbao*, the transnational dimension of the foreign press underwent significant changes over time, with a similar trend towards heightened exchanges during the 1930s, followed by a return to national sentiments in the final decade of the Republic ([figure 22](#anchor-figure-22)). In the post-World War I period, the emphasis was on international relations, encompassing aspects such as the "international question," fear, disputes, peace, and conferences. However, it also carried transnational connotations through terms like "international city," referring to a "contact zone" that facilitated interactions among different nationalities, and "international journalist," denoting a border crosser. In the subsequent decade, there persisted an ambiguity between the two poles of transnational and international. The primary focus was on the establishment of the International Club, a multinational non-state organization aimed at promoting international friendship, initiated in 1936 with the support of various Rotary members. Alongside this initiative, Rotary lectures prominently featured terms associated with diplomatic relations and international trade. Other terms that leaned toward the "transnational" dimension encompassed the Tennis Cup, Rotary International, and less common expressions like "international character”. The last period, encompassing the wartime and post-war era, is characterized by more impersonal terms such as payments, news, situation, and balance. The discourse in this period clearly emphasized differences rather than points of contact.

```R jdh={"object": {"source": ["Most frequent bigrams by decade in the English-language corpus, using TF-IDF as the metric."], "type": "image"}} tags=["figure-22", "anchor-figure-22"]
library("IRdisplay")
display_jpg(file="./media/Fig22.JPG")
```

In the subsequent section, I apply the same methodology to analyse the public roles of the Rotary Club and to compare the concepts utilized in the Chinese and English presses for delineating the public sphere throughout the three decades under examination.


### Shaping the Public


#### The Chinese Press: Promoting Social Welfare, Advertising Public-Spirited Organizations


The following table lists the most frequent terms based on *gong* 公 (public) in the *Shenbao* Rotary corpus ([table 36](#anchor-table-36)).

<!-- #region jdh={"object": {"source": ["Most frequent \u516c (gong)-based terms in the Shenbao Rotary corpus, based on simple frequency count. The highlighted terms are the most akin to the concept of the public sphere."], "type": "table"}} tags=["hermeneutics", "table-36", "anchor-table-36"] -->
| **Term**         | **Translation**  | **Count** | **Term**        | **Translation**      | **Count** |
|------------------|------------------|-----------|-----------------|----------------------|-----------|
| 公司 (Gongsi)    | Company          | 107       | 公展 (Gongzhan) | Public exhibition    | 4         |
| 公開 (Gongkai)   | Public (open)    | 18        | 公路 (Gonglu)   | Highway              | 4         |
| **公共 (Gonggong)**  | **Public (common)**  | 17        | **公民 (Gongmin)**  | **Citizen**              | 3         |
| 公映 (Gongying)  | Public screening | 13        | 公無 (Gongwu)   | Publicly nonexistent | 3         |
| 公會 (Gonghui)   | Association      | 12        | 公爵 (Gongjue)  | Duke                 | 3         |
| 公宴 (Gongyan)   | Public banquet   | 9         | **公用 (Gongyong)** | **Public use**           | 3         |
| **公衆 (Gongzhong)** | **The public**       | 9         | **公益 (Gongyi)**   | **Public welfare**       | 3         |
| 公子 (Gongzi)    | Young master     | 7         | 公僕 (Gongpu)   | Public servant       | 2         |
| 公園 (Gongyuan)  | Public park      | 6         | 公墓 (Gongmu)   | Public cemetery      | 2         |
| 公使 (Gongshi)   | Envoy            | 4         | 公權 (Gongquan) | Public power         | 2         |
<!-- #endregion -->

Contrary to the *guo*-based collocates, the collocates of terms associated with *gong* (public) form a highly fragmented network, revealing the multiplicity of potential meanings and dimensions of the term in the *Shenbao* newspaper ([figure 23](#anchor-figure-23)). The most substantial cluster revolves around four predominant terms: *gongkai* 公開 (open), *gonghui* (公會), *gongyi* (公益), and *gongmin* 公民 (literally, citizen; in this context, civic). This semantic constellation pertains to public meetings (*gonghui*, *gongkai*) or exhibitions (*zhanlan*) sponsored by the Rotary Club and other associations (*gongmin*, *gonghui*), dedicated to public welfare (*gongyi*). In *Shenbao*, the character “公” (*gong*, public) most frequently appeared in the compound 公開 (*gongkai*), such as in the expressions 公開餐會 (*gongkai canhui*) or 公開聚餐會 (*gongkai jucanhui*), designating Rotary’s meetings open to the public (public luncheon or public dinner party). These were distinguished from closed meetings (*bugongkai huiyi* 不公開會議) restricted to club members, usually focused on the induction of new members and internal discussions of club affairs. Public meetings typically featured a guest speaker, often a publicly known personality, delivering a speech on a subject of particular importance, such as the guest speaker from the Institute of Pacific Relations (Taipingyang guojiao taolunhui 太平洋國交討論會) (SPSP192909191506), or Fukushima’s talk on the situation in Japan, illustrated by a slide show (SPSP192911071520). In addition to lectures, open meetings encompassed entertaining events like Rotary’s Father and Son (*gongzi* 公子) or Father and Daughter Day (*nü gongzi lihui* 女公子蒞會) (SPSP192802181602, SPSP193006051424, SPSP194110140803), dinner dances open to Rotarians’ families, charity balls, and sports competitions (tennis, boxing) organized for fundraising purposes (SPSP193609261612).

```R jdh={"object": {"source": ["Network graph displaying the most frequent collocates of \u516c-based terms in the *Shenbao* Rotary corpus. Only collocates with a weight equal or exceeding 2, calculated using pairwise count per document, are displayed. The colour gradient reflects eigenvector centrality. Node size corresponds to the frequency of each term in the corpus. For precise figures on weight and frequency, refer to the attached tables. The code is accessible on the Github repository."], "type": "image"}} tags=["figure-23", "anchor-figure-23"]
library("IRdisplay")
display_jpg(file="./media/Fig23.JPG")
```

Public welfare primarily involves the promotion of public health and the eradication of poverty. Specifically, the term *gongyi* 公益 appeared in connection with philanthropic activities sponsored by the Rotary Club and other associations or individuals, such as Fei Wusheng 費吳生, a Chinese American citizen born in Suzhou, president of his local Rotary Club, portrayed as being “fervently dedicated to public welfare initiatives” (*Fei jun wei Mei ji zi you shengzhang Suzhou zaihua duiyu gongyi shiye jiwei rexin* 費君爲美籍自幼生長蘇州在華對於公益事業極爲熱心) (SPSP192306131801). After WWII, 公益 was specifically associated with a campaign against the habit of spitting among the public, presented as not only a visual nuisance but also a potential source of disease transmission. The campaign was launched by Lu Meiseng, president of the Public Welfare Society (Gongyi xiejinshe 公益協進社), in cooperation with other voluntary associations (SPSP194711070401). In this specific context, the term *gongmin* 公民 referred to civic associations such as the Civic education group (Gongmin jiaoyutuan 公民教育團) organized in 1927 (SPSP192705241014) and the Women's Civic Association (Funü gongmin huishe 婦女公民會社) devoted to youth and education (SPSP193705222001). This term helps to connect public welfare (*gongyi* 公益) with municipal cemeteries (*gongmu* 公墓) mentioned in Wu Liande’s talk advocating for cremation as an essential tool toward reducing the spread of disease and saving urban space (SPSP193606201501). This connection highlights cooperative practices between civil society and local authorities in the promotion of public welfare.


The second, smaller cluster is centered on *gonggong* 公共 (concessions) and *gongzhong* 公衆 (literally, people). The term 公共 in this context principally refers to the Chinese designation of the foreign concessions (gonggong zujie 公共租界) in Shanghai. It appeared mostly in connection with public health campaigns (*gonggong fasheng* 公共發生, *gonggong weisheng* 公共衛生), specifically against tuberculosis, tropical diseases, or opium addiction, and infrastructural projects (*gonggong jianshe* 公共建設). While Rotary Club’s concern for public health reflects the numerical importance of medical professionals among members of Rotary Clubs, infrastructural projects involved more specifically the Y’s Men Club, a sister organization modelled after the Rotary Club and shared similar missions. The connection between *gonggong* 公共 and *gongzhong* 公衆 in this cluster indicates the degree of cooperation between municipal authorities (primarily the SMC) and local elites toward the shared goal of solving social problems that were deemed detrimental to the community, principally reducing visible poverty and ensuring public safety. The most exemplary example of such cooperation is the “beggar camp” built during the Sino-Japanese war to cope with the massive influx of refugees in the foreign settlements. As seen earlier, this cooperation involved the Rotary Club, the Salvation Army, the SMC Public Works department (Gonggong zujie gongbuju 公共租界工部局), and the Municipal Police (Gonggong gongzujie jingwuchu 公共共租界警務處). The term *gongzhong* 公衆 essentially refers to public projects devoted to the benefit of society (*Gongzhong shiye nuli chouhua* 公衆事業努力籌劃) and “relief work of great public importance” (*Gongzhong qizhong zhijiu jishi shi gongzuo* 公衆綦重之救濟實施工作). It is often used in compound terms like public donations (*gongzhong juankuan* 公衆捐欵), such as those received to build a school for poor Russian children, or public contributions (*gongzhong kangkai* 公衆慷慨, *gongzhong zhijuanzhu* 公衆之捐助) to build the beggar camp during the war. It also appears in a lecture addressing the relations between the police and the public (*Zhiji ji gongzhong zhi gengshan baohu guanxi* 指即及公衆之更善保護關係). In general, the term 公衆 serves to designate the lower strata of society (masses or populace), commonly associated with poverty and criminality.


Other terms are less prominent and form separate clusters. Intriguingly, political connotations of the term “public” are insignificant in *Shenbao*. As highlighted earlier, the term *gongmin* 公民 refers to civic associations rather than the concept of a citizen. The term *gongju* 公舉 (public election or voting) in this context refers to the method used for selecting the winner of the Shanghai Queen Contest (Shanghai huanghou jingxuan 上海皇后競選), a beauty contest organized by the Rotary Club for fundraising purposes. The term “public opinion” (*gonglun* 公論) appeared only once in the compound name 公論報 (Gonglunbao), the name of a newspaper that sent a representative to attend US Senator Bingham’s lecture before the Rotary Club (SPSP192708051409). While the term “public opinion” is almost invisible in *Shenbao*, by contrast, it is the most prominent public-based bigram in the English corpus. Similarly, the term *gongyong* 公用 (public utilities) appeared only twice in *Shenbao*, whereas it is the second most prominent in the English press. In *Shenbao*, 公用 appears in the compound term “Bureau of Public Utilities” (Gongyong ju 公用局), in reference to their directors Xu Peihuang 徐佩璜 in the Chinese municipality (SPSP193310141010) and Robert McMullen in the International Settlement.


```R jdh={"object": {"source": ["Most frequent two-character \u516c-based terms by decade in the *Shenbao* corpus, using TF-IDF as metrics."], "type": "image"}} tags=["figure-24", "anchor-figure-24"]
library("IRdisplay")
display_jpg(file="./media/Fig24.JPG")
```

#### The Foreign Press: Nurturing Public Opinion, Developing Urban Amenities


As previously indicated, the semantic portrayal of the term "public" in the foreign press differs significantly from that in *Shenbao* ([table 37](#anchor-table-37)).

<!-- #region jdh={"object": {"source": ["Most frequent bigrams associated with 'public' in the ProQuest corpus, by decade, based on simple frequency. The highlighted terms are those that most closely refer to the abstract concept of the public sphere."], "type": "table"}} tags=["hermeneutics", "table-37", "anchor-table-37"] -->
| **Bigram**          | **Count** | **Bigram**            | **Count** | **Bigram**        | **Count** |
|---------------------|-----------|-----------------------|-----------|-------------------|-----------|
| **public opinion**  | **36**    | public utility        | 5         | **public debate** | **2**     |
| public health       | 28        | public announcement   | 4         | public demand     | 2         |
| public safety       | 16        | public education      | 4         | public function   | 2         |
| public school       | 13        | public vehicle        | 4         | public garden     | 2         |
| **public spirited** | **11**    | public administration | 3         | public inspection | 2         |
| **public affairs**  | **9**     | public enemy          | 3         | public lavatories | 2         |
| **public service**  | **8**     | public library        | 3         | public loan       | 2         |
| public utilities    | 8         | public life           | 3         | public relations  | 2         |
| public welfare      | 8         | public meeting        | 3         | public services   | 2         |
| public park         | 7         | public rickshaw       | 3         | public speaking   | 2         |
| public puller       | 6         | public organization   | 3         | **public spirit** | **2**     |
| public attention    | 5         | public address        | 2         | public support    | 2         |
| public bodies       | 5         | public building       | 2         |                   |           |
<!-- #endregion -->

The subsequent graph, illustrating the most prevalent collocates linked to the prominent bigrams formed with the term "public," outlines three primary senses of the public or three semantic clusters, which are partially interconnected. These clusters intersect with the operational modes of Rotary that were identified in the initial section ([figure 25](#anchor-figure-25)).

```R jdh={"object": {"source": ["Network graph illustrating the most frequent collocates of public-based terms in the English-language corpus. Only collocates with a weight exceeding 5, calculated using pairwise count per document, are displayed. The colour gradient reflects eigenvector centrality. Node size corresponds to the frequency of each term in the corpus. For precise figures on weight and frequency, refer to the attached tables."], "type": "image"}} tags=["figure-25", "anchor-figure-25"]
library("IRdisplay")
display_jpg(file="./media/Fig25.JPG")
```

The predominant cluster centers around the term "public opinion," establishing connections with a diverse array of terms. This cluster denotes the "forum" function fulfilled by both the Rotary Club and the press, acting as a conduit between the local, national, and international spheres. On one hand, the concept of public opinion is primarily associated with various lectures conducted during Rotary meetings. These lectures delved into the topic of public opinion in Western countries, notably the United States, concerning the political landscape in China, international peace, and other pertinent issues. Such lectures embodied Rotary's central mission of disseminating knowledge and fostering spaces for discussion and the exchange of perspectives.


While the physical attendance of Rotary meetings may be limited to a select few, detailed reports on the content of these lectures were published in newspapers, ensuring that the broader readership was informed. Certain readers extended these discussions beyond Rotary meetings by utilizing foreign newspapers, particularly through sections like "Correspondence" or "Letter to the Editor." For instance, an informed reader responded to Dr. Huang Zifang 黄子方 (1899-1940)'s lecture on the prevention of venereal disease, he believed emphasizing a crucial point that was either overlooked or downplayed during the lecture—social, cultural, or religious taboos on sexuality. According to this reader, these taboos constituted a significant impediment to educating the public and fostering appropriate behaviours (1425493444, 1371783031). In this context, the term "public opinion" underscores the role of the foreign press as a vital platform for local elites to express their opinions regarding municipal policies and other societal issues at the city level. This subcluster is characterized by a set of terms that act as a bridge between the broader "public opinion" cluster and other clusters, particularly the public utilities cluster.

<!-- #region citation-manager={"citations": {"": []}} -->
The second, smaller cluster centred on “public utilities” overlaps with Rotary’s mission of promoting social welfare and emphasizes its primary anchorage in urban settings. While this cluster is connected to the “public opinion” cluster through shared terms like Shanghai, government, world, foreign, general, it also has its own set of terms, referring to the local level of municipal administration and taking account of Chinese municipalities outside Shanghai (city, mayor, Nanking). This cluster delineates specific areas of municipal intervention (waterworks, economic development) and highlights the role of private actors (company, commercial) which were engaged in public policies. As I have showed in my previous research on outdoor advertising in Republican Shanghai, the public and private realms often cooperated in the development of public amenities (<cite data-cite="626961/RZEKCMV6"></cite>).
<!-- #endregion -->

The third, more fragmented cluster encompasses more general terms (public welfare, public affairs, public service, public spirit), concurrently related to practical operations (public utilities) and the more abstract concept of public opinion. The term "public welfare" serves as a link between the local (public bureau) and the national sphere, connecting with public opinion. Public welfare was a primary focus of the newly established Bureau of Social Affairs of the Chinese municipal government, as noted by its director Cai Zhengya 蔡正雅 (1420035311). In Nanjing, the mayor envisioned public welfare as a collaboration between the municipality and charity organizations to combat "social evils" such as opium smoking, gambling, and prostitution (1416677367). Public welfare also emerged as a professional specialization, mentioned in reference to individuals such as Paul Sung (Song Ruhai 宋如海), a member of the Hankow Rotary Club, portrayed in the 1934 *Who's Who of China* as a "public welfare worker" (1371489116). The Rotary Club itself utilized the press to reaffirm its commitment to public welfare through various actions, such as sponsoring a school for the blind, providing scholarships to study in America, and improving the street numbering system in Shanghai. Similarly, the club used the press to emphasize its interest in public affairs, particularly in housing and other urban reforms.


The term "public affairs" serves to bridge the political and market aspects of the public, with a focus on the American perspective. This is highlighted by the translation of Chinese diplomat Shi Zhaoji's impressions on American democracy after his return from the United States in 1929. "Public service" is associated with various subjects, including a lecture on the role of the press in China in 1924, the Catholic Congress in 1933-1936, rickshaw reforms in the mid-1930s, and the appointment of the Australian trade commissioner to Japan in 1935, who was said to have been in "public service" of the Australian government for many years. The expression "public spirit" or "public spirited" appears in connection with a range of topics, including international peace (threatened by Japan aggression), economic and business development (national reconstruction, tourism), social affairs and relief work (public health, housing, Salvation Army). In 1931, James Davidson, former vice-president of Rotary International, drew a connection between public-spirited organizations like the Rotary Club and the role of the press in commenting on "public affairs." The speaker further emphasized the Rotary Club's mission of enlightening people and promoting peace, defining the dissemination of knowledge as a civic duty for Rotarians (1418921614).


In contrast to *Shenbao*, where no clear semantic shifts occurred ([figure 24](#anchor-figure-24)), the contours of the public in the foreign press demonstrated significant changes over time ([figure 26](#anchor-figure-26)). Using TF-IDF as a metric, it appears that during the entire period, the most frequent bigrams revolved around the notion of public space in the city, rather than the abstract concepts of the public sphere. The post-WWI decade is centered on urban management and public amenities in the city, expressed through terms like public garden, public park, public policies, or public services. The following decade focuses on rickshaw reform, traffic management, and related problems (safety, public utilities, public vehicles, public works). This period also witnessed the rise of more psychological connotations such as "public spirited," which primarily served to qualify exemplary individuals or civic organizations. During the final period, no specific expression clearly emerged. Abstract terms like "public attention" and "public spirited" were losing momentum, while practical issues related to public health, refugees (public camp), and transportation (public bus) maintained their prominence.

```R jdh={"object": {"source": ["Most frequent bigrams associated with 'public' by decade in the ProQuest corpus, using TF-IDF as metrics."], "type": "image"}} tags=["figure-26", "anchor-figure-26"]
library("IRdisplay")
display_jpg(file="./media/Fig26.JPG")
```

To summarize, the Rotary Club served as a bridge between the different senses of the public, reflecting its dual commitment to international peace and local community service through two main operating modes: fundraising campaigns and philanthropic actions aimed at promoting public welfare, and lectures and debates aimed at disseminating knowledge and exchanging ideas among elites. The concept of the public, as defined by the foreign press, manifested a stronger transnational dimension compared to *Shenbao*. It devoted more space to public opinion in foreign countries regarding the situation in China and global issues, as well as public amenities aimed at improving business conditions and the comfort of urban elites in foreign settlements. Instead of focusing on civic associations, the foreign press emphasized the role of municipal authorities, primarily the Shanghai Municipal Council (SMC). From 1927 onwards, however, the foreign press paid greater attention to the newly established Chinese municipality in Shanghai and Nanjing, increasingly highlighting the importance of cooperation between municipal administration and public-spirited organizations such as the Rotary Club.


## Conclusion


Due to its transnational nature, focus on public welfare, and reliance on the local press to publicize its activities, the Rotary Club serves as an ideal lens for examining the formation of a transnational public sphere in Republican China. Through its missions and operational modes, the Rotary Club contributed to shaping a dual definition of the public sphere. On one hand, its meetings and lectures facilitated the exchange of ideas and the dissemination of knowledge, enabling educated individuals to form their own opinions on the modern world. In this sense, the Rotary's public sphere aligns with Habermas' conception of the "bourgeois" public sphere, a dimension more prominently represented in the English-language press than in the Chinese-language press. On the other hand, despite being an elite organization, the Rotary Club, like many elite organizations, engaged in various philanthropic endeavours aimed at promoting social welfare (*gongyi* 公益). Consequently, the business and professional elites involved in the Rotary sphere interacted with a broader, popular conception of the public that encompassed the lower strata of society (*gongzhong* 公眾). Moreover, these emerging elites extensively utilized the press to define their public roles and legitimize their privileged position in the global capitalist order, thereby contributing to the creation of new social divisions and economic inequalities within Chinese society during the Republican era. Reflecting a potential disenchantment with the republican regime, the sense of public welfare supported by voluntary organizations like the Rotary Club prevailed over more explicitly political dimensions of the public expressed through concepts such as citizenship or public opinion. Disillusioned with politics, non-state organizations like Rotary Clubs carved out their own privileged spaces for debates and exchanges of opinions, evident in the form of lectures and tiffin meetings. Additionally, the perceived failure of government institutions at both national and international levels to maintain political stability, safeguard international peace, and address economic and social problems prompted elites in China to turn to local and translocal forms of public engagement.


While the contemporary newspapers did not explicitly use the terms "transnational" or "transnationalism," the transnational nature of the public sphere manifested through the diverse activities of the Rotary Club, encompassing multiple dimensions that evolved over time and varied across languages. Both the Chinese- and English-language presses focused on international relations and the pursuit of international peace among nations, a key principle of the Rotary Club often discussed in lectures and public meetings. *Shenbao*, the Chinese-language newspaper, emphasized transpacific exchanges and Chinese border crossers, highlighting the interconnectedness with regions like Southeast Asia. In contrast, the foreign press, particularly the English-language newspapers, concentrated primarily on multinational encounters in foreign settlements, viewing them as crucial modes of transnational exchanges. These differences in focus reflected the newspapers' reliance on distinct sources of information and the diverse interests of their readership. Readers of the English-language press were typically foreigners or foreign-educated Chinese elites, primarily concerned with the situation in foreign settlements, the lives of foreign communities in treaty ports, and news from their homelands in Europe, North America, and colonial empires. Foreign newspapers had established extensive networks of correspondents and relied on connections with Western newspapers to access information not readily available to Chinese newspapers. On the other hand, readers of the Chinese press were more concerned with news affecting overseas Chinese communities in Southeast Asia, Australia, and America, where significant numbers of Chinese individuals had emigrated since the 19th century for labour, business, or educational purposes. The transnational Chinese diaspora provided a valuable network of correspondents that Chinese homeland newspapers could tap into, offering up-to-date information to their readers. Furthermore, representatives of Chinese newspapers often received invitations to attend business meetings not open to foreign reporters, such as those organized by the China Business Management Association (Zhongguo gongshang guanli xiehui) modeled after the Rotary Club. They also accompanied Chinese business delegations abroad, such as the Philippines Tour Group in 1936 or the delegation from Burma during the Sino-Japanese War, offering unique perspectives and access to events not readily available to foreign press representatives.

<!-- #region citation-manager={"citations": {"": []}} -->
Semantic analysis reveals that English-language periodicals emphasized verbal expressions of the public regarding both local and global issues, aligning with the forum function of both the Rotary Club and the press. In contrast, *Shenbao* placed a stronger emphasis on pragmatic actions taken by non-state organizations, reflecting Rotary's commitment to community service and elites' practices of using the periodical press to publicize philanthropic projects. The foreign press, particularly the English-language periodicals, highlighted the role of local authorities, primarily the Shanghai Municipal Council (SMC), reflecting the Council's personal connections with Rotary. Several SMC representatives were members of the club, and SMC members were frequently invited to lecture on their areas of expertise. Since its founding in 1854, the SMC was tasked with maintaining an environment conducive to business (<cite data-cite="626961/793ZT442"></cite>), and foreign elites in Shanghai traditionally relied on the SMC to manage urban affairs and social matters in the International Settlement. Conversely, the Chinese press placed a stronger emphasis on the roles of voluntary associations and local elites in taking charge of public welfare. These actions were a continuation of longstanding practices of elite activism since the late Qing dynasty but were also influenced by a novel American-inspired ethics of public service. Nevertheless, *Shenbao* increasingly highlighted Rotary's cooperation with the newly established local authorities. After the creation of the Chinese municipality in Shanghai in 1927, Chinese Mayor Wu Tiecheng took a keen interest in the club, and representatives of the Chinese municipal administration were regularly invited to give lectures on their areas of expertise. Similar connections between Chinese authorities and Rotary clubs developed in other cities as well, including Qingdao, Nanjing, and Chongqing during the Sino-Japanese War. After the outbreak of the war, *Shenbao* underscored Shanghai elites' cooperation with the SMC to address the significant challenge posed by the massive influx of refugees in Shanghai's foreign settlements.
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"": []}} -->
In the 1930s, the Chinese and foreign presses found common ground in their interest in multinational encounters, including international conventions and sports competitions, which proliferated during this decade. They also shared concerns about the currency crisis brought about in China by the global depression. Despite the disruptions caused by the war in both the Rotary Club and the press industry, foreign and Chinese newspapers continued to align during the war, particularly around the refugee problem and China-US trade relations. However, they diverged again after the war, with *Shenbao* becoming increasingly critical of the American policy of rebuilding Japan during the emerging Cold War. Moreover, internal tensions within the Rotary Club, not publicized in the press, led to the club splitting into separate Chinese- and English-speaking clubs after the war (<cite data-cite="626961/4YPDTCZE"></cite>). This highlights significant disparities between the narrative constructed from archival materials and the story presented in the press. While language and cultural barriers between foreign-educated and other Chinese elites emerged as a prominent concern in archival records, these issues were scarcely evident in the local press. The public facade that Rotary leaders aimed to present portrayed unity and social harmony, especially during those troubled times. Both the Chinese and English-language presses converged in shaping the image of an organization entirely devoted to promoting international goodwill among its members, concealing internal tensions that remained hidden in archival records. This corpus-driven investigation of the bilingual press therefore provides a valuable supplement and counterpoint to previous research based on Rotary archives (<cite data-cite="626961/4YPDTCZE"></cite>). Conversely, delving into archival materials and constructing a prosopography of Rotary members proved essential for interpreting the news delivered in the press on their subject. This reinforces the notion that computational approaches will not replace more traditional methods of archival research; instead, the two methods are most fruitfully employed when they complement and reinforce each other.
<!-- #endregion -->

Behind the public facade of unity and social harmony that Rotary elites aimed to build, this study has uncovered the hidden ideological dimension of both concepts—public and transnational—and the unequal power relations they concealed. Debates on tariff reform, the silver crisis, and unbalanced foreign trade in the 1930s echo the remnants of the "unequal treaties" system. Power relations are also evident in the hierarchical system of knowledge established in Rotary lectures, reflecting China's reliance on foreign or foreign-educated Chinese experts during the Republican era, with Chinese elites without foreign experience remaining underrepresented, particularly in the foreign press. Unequal power relations also manifest in asymmetries of information accessible to newspaper editors and readers. As mentioned earlier, the foreign press had access to information that the Chinese press did not, and vice versa. These asymmetries created a division among newspaper readers based on their language skills. Western-educated Chinese or foreign residents fluent in the Chinese language, who could read both presses, had access to a more comprehensive range of information and viewpoints. Aside from unequal relations among nations and nation-based groups, power relations within Chinese society should not be overlooked. Lastly, unequal relations between elites and non-elites were consistently evident through Rotary's commitment to public welfare and its campaigns in favour of the poor, the ill, and the weak. These widely publicized operations helped legitimize the social function of Rotary and enhance the reputation of its members.

<!-- #region tags=["hermeneutics"] -->
This paper has developed a methodology that integrates topic modeling with other computational techniques, such as named entity recognition (NER), geographical information systems (GIS), network analysis and visualization, to enhance historical research. One notable contribution is the introduction of an iterative topic modeling method, involving multiple successive iterations to gradually refine the study corpus and achieve a higher-quality corpus suitable for more in-depth analysis. This research emphasizes the significance of combining topic modeling with contextual knowledge and close reading of documents for a proper interpretation of observed topics, aligning with recommendations from previous studies. Furthermore, the paper showcases the value of combining topic modeling with other relevant methods to yield more substantial analytical insights. For instance, named entity recognition and network analysis were employed to analyze the configurations of actors and topics across languages and over time. GIS was used to map the geographic imaginations of newspaper readers in Shanghai, while co-occurrence networks were utilized to compare the semantic constellations of the transnational public sphere in the English and Chinese presses.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The challenges associated with working with digitized newspapers should not be underestimated. Besides the sheer size of digitized corpora, which represents a "big data deluge," for scholars accustomed to close reading of archival materials, this paper addresses one of the main challenges in dealing with digitized newspapers—namely, extracting appropriate news items within individual documents. The definition of the relevant unit of analysis is a crucial prerequisite for topic modeling and text mining, yet this step is often overlooked or briefly mentioned in scholarly publications. The challenge is particularly pronounced for scholars of modern China who rely on commercial publishers for digitized collections. These publishers may not adhere to the "best practices" typically followed by public libraries and cultural heritage institutions in Europe and North America. Inconsistencies and variability in data quality further complicate the work of historians. The guidelines and algorithms used by commercial providers for digitization, pre-processing, and metadata creation are often opaque, hindering historians' engagement with "digital hermeneutics" (<cite data-cite="626961/75E7A2UI"></cite>). While this paper may not provide definitive conclusions, it represents a significant step in acknowledging these challenges and makes a genuine attempt to offer ad hoc solutions to remedy the most problematic obstacles.

To conclude, the author advocates for a closer collaboration between historians and computer scientists to enhance digitized corpora and improve data quality for historical research. This collaboration is crucial for identifying problems and devising solutions upstream, aimed at reducing the time and effort spent on pre-processing and cleaning data, and allowing researchers to focus on analysis and interpretation. While the HistText application represents a significant advancement in using computational methods for historical research, there is still room for improvement. The author suggests three key areas for future collaborative work. First, refining text segmentation to define semantically coherent text units beneath the level of articles is essential for increasing the precision and accuracy of historical analyses. This involves moving beyond the preliminary topic modeling method based on concordance and the manual segmentation used for subsequent analyses of actors and concepts, especially when dealing with large corpora. Second, entity linking is crucial for facilitating the identification of persons and organizations, reducing the time and effort spent on disambiguating names, and standardizing variants across articles, periods, and languages. Finally, the automatic alignment of terms and topics across languages would enable cross-lingual comparisons and a more systematic study of news circulations across periodicals and linguistic communities.
<!-- #endregion -->

## Appendix

<!-- #region tags=["hermeneutics", "anchor-appendix"] -->
In the following tables, *SB* stands for *Shenbao*, PQ = ProQuest. 5T = 5-topic model, 10T = 10-topic model, 20T = 20-topic model. The number immediately following indicates the number of the topic in each topic model.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Tables 1 to 6 provide a summary of the topics for each model, including their label, the 10 most frequent words defining each topic, and their various attributes (topical group, dimension, proportion, and trend over time). Tables 7 and 8 display the topics aligned across models. Tables 9, 10, and 11 display the topics aligned across languages.
<!-- #endregion -->

### Summary of topic models

<!-- #region jdh={"object": {"source": ["Summary of topics for the 5-topic model in Chinese corpus."], "type": "table"}} tags=["table-1", "hermeneutics", "anchor-table-1"] -->

| TopicCode  | **TopicLabel**         | **TopWords**                                                     | **Proportion** | **Proportion%** | **Local** | **Functions** | **Trend**           |
|------------|------------------------|------------------------------------------------------------------|----------------|-----------------|-----------|---------------|---------------------|
| **SB5T01** | Children               | 玩具, 兒童, 醫院, 修理, 苦兒, 耶誕, 發起, 貧苦, 放映, 大戲院     |          0.129 | 13%             | Local     | SPONSOR       | Increase (dramatic) |
| **SB5T02** | International 國際     | 國際, 社員, 代表, 大會, 會員, 天津, 此次, 世界, 該社, 中外       |          0.226 | 23%             | Non-local | ORGANIZATION  | Stable              |
| **SB5T03** | All Nations 萬國       | 美國, 定於, 本週, 公司, 組織, 今日, 扶輪, 社長, 昨日, 萬國       |          0.201 | 20%             | Non-local | MEETING       | Increase (moderate) |
| **SB5T04** | Early meetings (1920s) | 舉行, 飯店, 演講, 下午, 十二時, 聚餐, 星期四, 聚餐會, 都城, 中午 |          0.239 | 24%             | Local     | MEETING       | Increase (moderate) |
| **SB5T05** | Wartime meetings       | 常會, 下午, 總會, 聯華, 乞丐, 大學, 十五日, 二時, 馬路, 四川     |          0.205 | 21%             | Local     | MEETING       | Decline (dramatic)  |

<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Summary of topics for the 5-topic model in the English corpus."], "type": "table"}} tags=["table-2", "hermeneutics", "anchor-table-2"] -->
| TopicCode  | **TopicLabel**                   | **TopWords**                                                                               | **Proportion** | **Proportion%** | **Local** | **Functions** | **Trend**           |
|------------|----------------------------------|--------------------------------------------------------------------------------------------|----------------|-----------------|-----------|---------------|---------------------|
| **PQ5T01** | Past tiffins (reports)           | shanghai, president, tiffin, members, meeting, held, yesterday, hotel,   weekly, rotarians |          0.209 | 21%             | Local     | MEETING       | Stable              |
| **PQ5T02** | Children                         | shanghai, children, hospital, toys, made, school, christmas, work,   committee, russian    |          0.154 | 15%             | Local     | SPONSOR       | Increase (dramatic) |
| **PQ5T03** | Lectures                         | nanking, address, foreign, said, subject, shanghai, delivered, speech,   told, government  |          0.213 | 21%             | Non-local | FORUM         | Increase (moderate) |
| **PQ5T04** | Boy scouts                       | shanghai, first, said, international, world, shield, present, work,   local, great         |          0.168 | 17%             | Local     | SPONSOR       | Decrease (moderate) |
| **PQ5T05** | Upcoming tiffins (announcements) | shanghai, meeting, american, held, hotel, thursday, members, weekly,   next, today         |          0.256 | 26%             | Local     | MEETING       | Decrease (dramatic) |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Summary of topics for the 10-topic model in the Chinese corpus."], "type": "table"}} tags=["table-3", "hermeneutics"] -->
| TopicCode   | **TopicLabel**        | **TopWords**                                                     | **Proportion** | **Proportion%** | **Functions** | **Local** | **Trend**           |
|-------------|-----------------------|------------------------------------------------------------------|----------------|-----------------|---------------|-----------|---------------------|
| **SB10T01** | Tiffins (Metropole)   | 舉行, 飯店, 演講, 美國, 聚餐會, 聚餐, 星期四, 十二時, 昨日, 都城 |          0.157 |           15.7% | MEETING       | Local     | Stable              |
| **SB10T02** | International 國際    | 國際, 世界, 大會, 演說, 代表, 會員, 組織, 親善, 精神, 日本       |          0.077 |            7.7% | FORUM         | Non-local | Increase (moderate) |
| **SB10T03** | Speeches              | 社員, 主席, 該社, 組織, 該會, 昨日, 各國, 本埠, 此次, 報告       |          0.081 |            8.1% | FORUM         | Mixed     | Decrease (dramatic) |
| **SB10T04** | Special events        | 舉行, 天津, 公司, 大會, 盛大, 招待, 本月, 對於, 此次, 出席       |          0.094 |            9.4% | MEETING       | Local     | Decrease (dramatic) |
| **SB10T05** | Tennis Cup            | 扶輪, 國際, 萬國, 比賽, 社長, 代表, 錦標, 中華, 市長, 參加       |          0.115 |           11.5% | MEETING       | Local     | Decrease (moderate) |
| **SB10T06** | Children              | 玩具, 兒童, 修理, 苦兒, 醫院, 耶誕, 貧苦, 放映, 徵求, 影片       |          0.067 |            6.7% | SPONSOR       | Local     | Increase (dramatic) |
| **SB10T07** | District elections    | 討論, 下午, 舉行, 區域, 博士, 年會, 昨日, 團體, 國際, 增加       |          0.051 |            5.1% | ORGANIZATION  | Non-local | Increase (dramatic) |
| **SB10T08** | Early meetings (1923) | 下午, 總會, 常會, 聯華, 大學, 二時, 馬路, 青年會, 協會, 四川     |          0.131 |           13.1% | MEETING       | Local     | Decrease (dramatic) |
| **SB10T09** | Beggar camp           | 乞丐, 救世軍, 本報, 工部局, 會議, 本市, 收容所, 希望, 慈善, 問題 |          0.091 |            9.1% | SPONSOR       | Local     | Increase (dramatic) |
| **SB10T10** | Wartime meetings      | 常會, 本週, 定於, 童子軍, 公司, 八日, 十八日, 十日, 十五日, 五月 |          0.138 |           
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Summary of topics for the 10-topic model in the English corpus."], "type": "table"}} tags=["table-4", "hermeneutics"] -->
| TopicCode   | **TopicLabel**          | **TopWords**                                                                                       | **Proportion** | **Proportion%** | **Functions** | **Local** | **Trend**           |
|-------------|-------------------------|----------------------------------------------------------------------------------------------------|----------------|-----------------|---------------|-----------|---------------------|
| **PQ10T01** | Elections               | shanghai, president, member, fong, international, secretary,   board, elected, past, harris        |          0.101 |           10.1% | Mixed         | ORGAN     | Decrease (moderate) |
| **PQ10T02** | Children                | children, hospital, toys, shanghai, christmas, made, funds,   charity, year, building              |          0.087 |            8.7% | Local         | SPONSOR   | Increase (dramatic) |
| **PQ10T03** | Non-Shanghai Clubs      | nanking, wang, international, foreign, hangchow, district,   affairs, president, special, minister |          0.067 |            6.7% | Non-Local     | ORGAN     | Increase (dramatic) |
| **PQ10T04** | Social work and workers | work, shanghai, public, committee, community, interest,   relief, church, municipal, service       |          0.099 |            9.9% | Local         | FORUM     | Increase (moderate) |
| **PQ10T05** | American community      | american, shanghai, states, united, university, america,   addressed, foreign, company, hongkong   |          0.107 |           10.7% | Mixed         | MEET      | Decrease (dramatic) |
| **PQ10T06** | Boy scouts              | school, shanghai, miss, russian, shield, scouts, ball, troop,   presented, boys                    |          0.078 |            7.8% | Local         | SPONSOR   | Decrease (moderate) |
| **PQ10T07** | Weekly meetings         | meeting, hotel, held, shanghai, weekly, thursday, tiffin,   metropole, speaker, yesterday          |          0.162 |           16.2% | Local         | MEET      | Increase (moderate) |
| **PQ10T08** | Special events          | members, tiffin, guests, shanghai, house, astor, rotarians,   party, held, dinner                  |            0.1 |             10% | Local         | MEET      | Decrease (dramatic) |
| **PQ10T09** | Sino-Japanese relations | address, japan, japanese, government, peking, delivered, last,   members, present, international   |          0.093 |            9.3% | Non-Local     | FORUM     | Stable              |
| **PQ10T10** | Lectures                | said, shanghai, world, years, address, speech, gave, talk,   members, editor                       |          0.105 |           10.5% | Non-Local     | FORUM     | Stable              |

<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Summary of topics for the 20-topic model in the Chinese corpus."], "type": "table"}} tags=["table-5", "hermeneutics"] -->
| TopicCode   | **TopicLabel**             | **TopWords**                                                         | **Proportion** | **Proportion%** | **Local** | **Functions** | **Trend**           |
|-------------|----------------------------|----------------------------------------------------------------------|----------------|-----------------|-----------|---------------|---------------------|
| **SB20T01** | 01 - Special events        | 昨日, 本埠, 舉行, 飯店, 報告, 該社, 代表, 中西, 主席, 來賓           |          0.045 |            4.5% | Mixed     | MEETING       | Decline (dramatic)  |
| **SB20T02** | 02 - International 國際    | 代表, 國際, 出席, 會議, 宗旨, 大會, 親善, 精神, 歡迎, 太平洋         |          0.044 |            4.4% | Non-local | ORGANIZATION  | Stable              |
| **SB20T03** | 03 - Meetings (brief)      | 演講, 下午, 都城, 飯店, 時間, 聚餐, 事項, 先生, 中午, 十二時         |          0.049 |            4.9% | Local     | MEETING       | Increase (dramatic) |
| **SB20T04** | 04 - Meetings (program)    | 常會, 本週, 定於, 舉行, 中午, 假座, 五月, 屆時, 星期四, 飯店         |           0.13 |             13% | Local     | MEETING       | Increase (dramatic) |
| **SB20T05** | 05 - Tennis Cup            | 扶輪, 比賽, 萬國, 錦標, 網球, 中華, 社長, 夫人, 體育, 網球賽         |          0.046 |            4.6% | Local     | MEETING       | Decline (moderate)  |
| **SB20T06** | 06 - Children (Entertain)  | 玩具, 苦兒, 耶誕, 放映, 影片, 主辦, 電影, 運動, 照例, 公映           |          0.026 |            2.6% | Local     | SPONSOR       | Increase (dramatic) |
| **SB20T07** | 07 - District elections    | 討論, 區域, 擴大, 一年, 進行, 下午, 博士, 一百, 增加, 成立           |          0.025 |            2.5% | Non-local | ORGANIZATION  | Increase (dramatic) |
| **SB20T08** | 08 - Early meetings (1923) | 總會, 常會, 下午, 聯華, 八日, 廿八日, 四川, 二時, 廿七日, 十五日     |          0.084 |            8.4% | Local     | MEETING       | Decline (dramatic)  |
| **SB20T09** | 09 - Boy Scouts            | 中外, 童子軍, 今日, 日本, 席間, 董事, 主席, 紀念, 昨在, 職員         |          0.052 |            5.2% | Local     | SPONSOR       | Increase (moderate) |
| **SB20T10** | 10 - Poor Russians         | 舉行, 本月, 盛大, 市長, 會員, 大華, 事務, 國際, 飯店, 本埠           |           0.05 |              5% | Local     | SPONSOR       | Decline (moderate)  |
| **SB20T11** | 11 - Not valid             | 美國, 都城, 飯店, 我國, 掉換, 光明, 各處, 國泰, 擁擠, 靜安寺         |          0.031 |            3.1% | Mixed     | OTHER         | Increase (dramatic) |
| **SB20T12** | 12 - Children (Hospital)   | 玩具, 兒童, 貧苦, 醫院, 修理, 破舊, 大戲院, 徵求, 各界, 一件         |          0.043 |            4.3% | Local     | SPONSOR       | Increase (dramatic) |
| **SB20T13** | 13 - Rotary abroad (國際)  | 大會, 國際, 該會, 法國, 成立, 會員, 公司, 主席, 精神, 舉行           |          0.027 |            2.7% | Non-local | ORGANIZATION  | Stable (unique)     |
| **SB20T14** | 14 - Speeches              | 舉行, 本報, 主席, 美國, 委員會, 社友, 年會, 會員, 馬來, 視察         |          0.041 |            4.1% | Mixed     | FORUM         | Increase (dramatic) |
| **SB20T15** | 15 - Tianjin Rotary        | 天津, 國際, 香港, 八十一, 學生, 十五日, 此次, 福州, 歡迎, 對於       |          0.044 |            4.4% | Non-local | ORGANIZATION  | Decline (moderate)  |
| **SB20T16** | 16 - Tiffins (Carlton)     | 聚餐會, 舉行, 飯店, 十二時, 聚餐, 美國, 演講, 星期四, 三十分, 今午   |          0.083 |            8.3% | Local     | MEETING       | Decline (dramatic)  |
| **SB20T17** | 17 - Beggar Camp           | 乞丐, 救世軍, 工部局, 問題, 委員會, 收容所, 俱樂部, 本市, 租界, 救濟 |           0.06 |              6% | Local     | SPONSOR       | Increase (dramatic) |
| **SB20T18** | 18 - Hangzhou Rotary       | 下午, 大學, 四時, 八時, 杭州, 十三日, 協會, 華人, 租界, 二時         |           0.05 |              5% | Non-local | ORGANIZATION  | Decline (dramatic)  |
| **SB20T19** | 19 - Peace resolution      | 社員, 演說, 及其, 各國, 組織, 此次, 發表, 該社, 國際, 團體           |          0.038 |            3.8% | Mixed     | FORUM         | Stable (unique)     |
| **SB20T20** | 20 - Rotary abroad (世界)  | 世界, 組織, 目的, 各國, 演說, 從事, 英國, 努力, 社員, 親善           |          0.029 |            2.9% | Non-local | ORGANIZATION  | Stable (unique)     |

<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Summary of topics for the 20-topic model in the English corpus."], "type": "table"}} tags=["table-6", "hermeneutics"] -->
| TopicCode   | **TopicLabel**                    | **TopWords**                                                                                      | **Proportion** | **Proportion%** | **Local** | **Functions** | **Trend**            |
|-------------|-----------------------------------|---------------------------------------------------------------------------------------------------|----------------|-----------------|-----------|---------------|----------------------|
| **PQ20T01** | 01 - Organization                 | shanghai, president, international, past, fong, member, local,   harris, fitch, george            | 0,04           | 4%              | Non-local | ORGANIZATION  | Stable               |
| **PQ20T02** | 02 - Children                     | hospital, toys, children, shanghai, christmas, charity, made,   year, funds, ward                 | 0,055          | 6%              | Local     | SPONSOR       | Increase (dramatic)  |
| **PQ20T03** | 03 - US & East Asia               | foreign, trade, arnold, week, addresses, julean, various,   commercial, members, commissioner     | 0,035          | 4%              | Non-local | FORUM         | Increase (dramatic)  |
| **PQ20T04** | 04 - Social work and workers      | work, committee, relief, public, shanghai, community,   international, done, interest, service    | 0,051          | 5%              | Local     | FORUM         | Increase (moderate)  |
| **PQ20T05** | 05 - American community           | american, shanghai, states, united, company, member,   addressed, thursday, university, commerce  | 0,063          | 6%              | Mixed     | MEETING       | Decrease (dramatic)  |
| **PQ20T06** | 06 - Boy scouts                   | school, shield, scouts, troop, russian, shanghai, president,   jamboree, camp, scout              | 0,031          | 3%              | Local     | SPONSOR       | Decrease (dramatic)  |
| **PQ20T07** | 07 - Blind school                 | shanghai, road, chang, institution, issue, work, building,   charge, official, appeal             | 0,038          | 4%              | Local     | SPONSOR       | Decrease (dramatic)  |
| **PQ20T08** | 08 - Weekly tiffins (Metropole)   | hotel, shanghai, meeting, held, weekly, metropole, thursday,   members, yesterday, speaker        | 0,095          | 10%             | Local     | MEETING       | Increase (dramatic)  |
| **PQ20T09** | 09 - Meetings announcements       | meeting, today, program, speak, regular, held, next, closed,   tomorrow, shang                    | 0,048          | 5%              | Local     | MEETING       | Increase (moderate)  |
| **PQ20T10** | 10 - Speeches (not valid)         | said, hongkong, recently, well, talk, pacific, institute,   great, read, speech                   | 0,05           | 5%              | Non-local | OTHER         | Increase (moderate)  |
| **PQ20T11** | 11 - Special events               | members, shanghai, dinner, evening, given, party, clock,   ladies, night, afternoon               | 0,054          | 5%              | Local     | MEETING       | Decrease (dramatic)  |
| **PQ20T12** | 12 - District conference          | wang, conference, district, hangchow, governor, members,   international, president, tsinan, held | 0,038          | 4%              | Non-local | ORGANIZATION  | Increase (dramatic)  |
| **PQ20T13** | 13 - Nanking Rotary Club          | nanking, government, national, bureau, affairs, soochow,   special, central, capital, minister    | 0,047          | 5%              | Non-local | ORGANIZATION  | Increase (dramatic)  |
| **PQ20T14** | 14 - Opinions (not valid)         | address, shanghai, delivered, present, last, speech, editor,   years, subject, history            | 0,076          | 8%              | Non-local | OTHER         | Increase (dramatic)  |
| **PQ20T15** | 15 - Poor Russians                | miss, shanghai, french, school, russian, children, girls,   society, race, donation               | 0,044          | 4%              | Local     | SPONSOR       | Increase (dramatic)  |
| **PQ20T16** | 16 - Games/Competitions           | shanghai, meet, international, first, radio, local, team,   tennis, american, presented           | 0,038          | 4%              | Local     | MEETING       | Decrease (moderate)  |
| **PQ20T17** | 17 - Weekly tiffins (Astor House) | tiffin, meeting, guests, held, address, members, gave, weekly,   yesterday, interesting           | 0,067          | 7%              | Local     | MEETING       | Decrease (dramatic)  |
| **PQ20T18** | 18 - Tientsin Rotary Club         | tientsin, left, peking, church, meeting, house, astor, union,   service, shanghai                 | 0,04           | 4%              | Non-local | OTHER         | Stable               |
| **PQ20T19** | 19 - Addresses (not valid)        | japanese, life, rotarians, rotarian, business, members, years,   first, great, said               | 0,044          | 4%              | Non-local | OTHER         | Increase (moderate)  |
| **PQ20T20** | 20 - Local elections              | president, general, elected, secretary, board, shanghai, year,   meeting, directors, chairman     | 0,046          | 5%              | Local     | ORGANIZATION  | Decrease (moderate)  |

<!-- #endregion -->

### Cross-model alignment

<!-- #region tags=["hermeneutics"] -->
Tables 7 and 8 display the topics aligned across models.
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Topics aligned across models in the Chinese corpus."], "type": "table"}} tags=["table-7", "hermeneutics"] -->
| 5TopicCode | **5TopicLabel**        | 10TopicCode | **10TopicLabel**      | 20TopicCode | **20TopicLabel**           |
|------------|------------------------|-------------|-----------------------|-------------|----------------------------|
| **SB5T01** | Children               | **SB10T06** | Children              | **SB20T06** | 06 - Children (Entertain)  |
| **SB5T01** | Children               | **SB10T06** | Children              | **SB20T12** | 12 - Children (Hospital)   |
| **SB5T02** | International 國際     | **SB10T02** | International 國際    | **SB20T02** | 02 - International 國際    |
| **SB5T03** | All Nations 萬國       | **SB10T05** | Tennis Cup            | **SB20T05** | 05 - Tennis Cup            |
| **SB5T04** | Early meetings (1920s) | **SB10T08** | Early meetings (1923) | **SB20T08** | 08 - Early meetings (1923) |
| **SB5T05** | Wartime meetings       | **SB10T10** | Wartime meetings      | **SB20T03** | 03 - Meetings (brief)      |
|            |                        | **SB10T01** | Tiffins (Metropole)   | **SB20T04** | 04 - Meetings (program)    |
|            |                        | **SB10T02** | International 國際    | **SB20T13** | 13 - Rotary abroad (國際)  |
|            |                        | **SB10T02** | International 國際    | **SB20T20** | 20 - Rotary abroad (世界)  |
|            |                        | **SB10T03** | Speeches              | **SB20T07** | 07 - District elections    |
|            |                        | **SB10T03** | Speeches              | **SB20T14** | 14 - Speeches              |
|            |                        | **SB10T04** | Special events        | **SB20T01** | 01 - Special events        |
|            |                        | **SB10T09** | Beggar camp           | **SB20T17** | 17 - Beggar Camp           |
|            |                        |             |                       | **SB20T09** | 09 - Boy Scouts            |
|            |                        |             |                       | **SB20T10** | 10 - Poor Russians         |
|            |                        |             |                       | **SB20T11** | 11 - Not valid             |
|            |                        |             |                       | **SB20T15** | 15 - Tianjin Rotary        |
|            |                        |             |                       | **SB20T16** | 16 - Tiffins (Carlton)     |
|            |                        |             |                       | **SB20T18** | 18 - Hangzhou Rotary       |
|            |                        |             |                       | **SB20T19** | 19 - Peace resolution      |

<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Topics aligned across models in the English corpus."], "type": "table"}} tags=["table-8", "hermeneutics"] -->
| 5TopicCode | **5TopicLabel**                  | 10TopicCode | **10TopicLabel**        | 20TopicCode | **20TopicLabel**                  |
|------------|----------------------------------|-------------|-------------------------|-------------|-----------------------------------|
| **PQ5T01** | Past tiffins (reports)           | **PQ10T07** | Weekly meetings         | **PQ20T08** | 08 - Weekly tiffins (Metropole)   |
| **PQ5T01** | Past tiffins (reports)           | **PQ10T07** | Weekly meetings         | **PQ20T17** | 17 - Weekly tiffins (Astor House) |
| **PQ5T02** | Children                         | **PQ10T02** | Children                | **PQ20T02** | 02 - Children                     |
| **PQ5T03** | Lectures                         | **PQ10T09** | Sino-Japanese relations | **PQ20T19** | 19 - Addresses (not valid)        |
| **PQ5T03** | Lectures                         | **PQ10T10** | Lectures                | **PQ20T10** | 10 - Speeches (not valid)         |
| **PQ5T04** | Boy scouts                       | **PQ10T06** | Boy scouts              | **PQ20T06** | 06 - Boy scouts                   |
| **PQ5T05** | Upcoming tiffins (announcements) | **PQ10T07** | Weekly meetings         | **PQ20T09** | 09 - Meetings announcements       |
|            |                                  | **PQ10T01** | Elections               | **PQ20T01** | 01 - Organization                 |
|            |                                  | **PQ10T01** | Elections               | **PQ20T12** | 12 - District conference          |
|            |                                  | **PQ10T01** | Elections               | **PQ20T20** | 20 - Local elections              |
|            |                                  | **PQ10T03** | Non-Shanghai Clubs      | **PQ20T13** | 13 - Nanking Rotary Club          |
|            |                                  | **PQ10T03** | Non-Shanghai Clubs      | **PQ20T18** | 18 - Tientsin Rotary Club         |
|            |                                  | **PQ10T04** | Social work and workers | **PQ20T04** | 04 - Social work and workers      |
|            |                                  | **PQ10T05** | American community      | **PQ20T05** | 05 - American community           |
|            |                                  | **PQ10T08** | Special events          | **PQ20T11** | 11 - Special events               |
|            |                                  |             |                         | **PQ20T03** | 03 - US & East Asia               |
|            |                                  |             |                         | **PQ20T07** | 07 - Blind school                 |
|            |                                  |             |                         | **PQ20T14** | 14 - Opinions (not valid)         |
|            |                                  |             |                         | **PQ20T15** | 15 - Poor Russians                |
|            |                                  |             |                         | **PQ20T16** | 16 - Games/Competitions           |
<!-- #endregion -->

### Cross-language alignment

<!-- #region jdh={"object": {"source": ["Topics aligned across languages for the 5-topic model."], "type": "table"}} tags=["table-9", "hermeneutics"] -->
| CHINESE   PRESS (SHENBAO) |                        | ENGLISH PRESS   (PROQUEST) |                                  |
|:-------------------------:|:----------------------:|:--------------------------:|:--------------------------------:|
| SB5T01                    | Children               | PQ5T02                     | Children                         |
| SB5T02                    | International 國際     |                            |                                  |
| SB5T03                    | All Nations 萬國       |                            |                                  |
| SB5T04                    | Early meetings (1920s) | PQ5T01                     | Past tiffins (reports)           |
| SB5T04                    | Early meetings (1920s) | PQ5T05                     | Upcoming tiffins (announcements) |
| SB5T05                    | Wartime meetings       | PQ5T01                     | Past tiffins (reports)           |
| SB5T05                    | Wartime meetings       | PQ5T05                     | Upcoming tiffins (announcements) |
|                           |                        | PQ5T03                     | Lectures                         |
|                           |                        | PQ5T04                     | Boy scouts                       |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Topics aligned across languages for the 10-topic model."], "type": "table"}} tags=["table-10", "hermeneutics"] -->
| CHINESE   PRESS (SHENBAO) |                       | ENGLISH PRESS   (PROQUEST) |                         |
|:-------------------------:|:---------------------:|:--------------------------:|:-----------------------:|
| SB10T06                   | Children              | PQ10T02                    | Children                |
| SB10T07                   | District elections    | PQ10T01                    | Elections               |
| SB10T04                   | Special events        | PQ10T08                    | Special events          |
| SB10T010                  | Tennis Cup            | PQ10T08                    | Special events          |
| SB10T08                   | Early meetings (1923) | PQ10T07                    | Weekly meetings         |
| SB10T01                   | Tiffins (Metropole)   | PQ10T07                    | Weekly meetings         |
| SB10T10                   | Wartime meetings      | PQ10T07                    | Weekly meetings         |
| SB10T03                   | Speeches              | PQ5T10                     | Lectures                |
| SB10T03                   | Speeches              | PQ10T09                    | Sino-Japanese relations |
| SB10T02                   | International 國際    | PQ10T09                    | Sino-Japanese relations |
| SB10T09                   | Beggar camp           | PQ10T04                    | Social work and workers |
| SB10T02                   | International 國際    | PQ10T05                    | American community      |
|                           |                       | PQ10T03                    | Non-Shanghai Clubs      |
|                           |                       | PQ10T06                    | Boy scouts              |
<!-- #endregion -->

<!-- #region jdh={"object": {"source": ["Topics aligned across languages for the 20-topic model."], "type": "table"}} tags=["table-11", "hermeneutics"] -->
| CHINESE   PRESS (SHENBAO) |                            | ENGLISH PRESS   (PROQUEST) |                                   |
|:-------------------------:|:--------------------------:|:--------------------------:|:---------------------------------:|
| SB20T01                   | 01 - Special events        | PQ20T11                    | 11 - Special events               |
| SB20T02                   | 02 - International 國際    | PQ20T01                    | 01 - Organization                 |
| SB20T03                   | 03 - Meetings (brief)      | PQ20T09                    | 09 - Meetings announcements       |
| SB20T04                   | 04 - Meetings (program)    | PQ20T08                    | 08 - Weekly tiffins (Metropole)   |
| SB20T05                   | 05 - Tennis Cup            | PQ20T16                    | 16 - Games/Competitions           |
| SB20T06                   | 06 - Children (Entertain)  | PQ20T02                    | 02 - Children                     |
| SB20T07                   | 07 - District elections    | PQ20T12                    | 12 - District conference          |
| SB20T07                   | 07 - District elections    | PQ20T20                    | 20 - Local elections              |
| SB20T08                   | 08 - Early meetings (1923) | PQ20T09                    | 09 - Meetings announcements       |
| SB20T09                   | 09 - Boy Scouts            | PQ20T06                    | 06 - Boy scouts                   |
| SB20T10                   | 10 - Poor Russians         | PQ20T15                    | 15 - Poor Russians                |
| SB20T11                   | 11 - Not valid             | PQ20T10                    | 10 - Speeches (not valid)         |
| SB20T11                   | 11 - Not valid             | PQ20T14                    | 14 - Opinions (not valid)         |
| SB20T11                   | 11 - Not valid             | PQ20T19                    | 19 - Addresses (not valid)        |
| SB20T12                   | 12 - Children (Hospital)   | PQ20T02                    | 02 - Children                     |
| SB20T13                   | 13 - Rotary abroad (國際)  |                            |                                   |
| SB20T14                   | 14 - Speeches              |                            |                                   |
| SB20T15                   | 15 - Tianjin Rotary        | PQ20T18                    | 18 - Tientsin Rotary Club         |
| SB20T16                   | 16 - Tiffins (Carlton)     | PQ20T17                    | 17 - Weekly tiffins (Astor House) |
| SB20T17                   | 17 - Beggar Camp           |                            |                                   |
| SB20T18                   | 18 - Hangzhou Rotary       | PQ20T13                    | 13 - Nanking Rotary Club          |
| SB20T19                   | 19 - Peace resolution      |                            |                                   |
| SB20T20                   | 20 - Rotary abroad (世界)  |                            |                                   |
|                           |                            | PQ20T03                    | 03 - US & East Asia               |
|                           |                            | PQ20T04                    | 04 - Social work and workers      |
|                           |                            | PQ20T05                    | 05 - American community           |
|                           |                            | PQ20T07                    | 07 - Blind school                 |
|                           |                            | PQ20T13                    | 13 - Nanking Rotary Club          |
<!-- #endregion -->

<!-- #region tags=["hidden"] -->
## Bibliography
<!-- #endregion -->

<!-- #region tags=["hidden"] -->
<div class="cite2c-biblio"></div>
<!-- #endregion -->

```R

```
