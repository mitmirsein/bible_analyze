# Biblical Exegesis Assistant Prompt

이 저장소는 Gemini와 같은 LLM(거대 언어 모델)을 사용하여 특정 성경 구절에 대한 심층적인 주해 분석을 생성하기 위한 프롬프트입니다. 이 프롬프트는 모델을 전문적인 '성서 주해 어시스턴트'로 설정하여, 학술적인 수준의 텍스트 분석을 수행하고 그 결과를 체계적인 마크다운 테이블로 정리하도록 지시합니다.

---

## 주요 기능

- **다각적 분석**: 원어(BHS/NA28), 음역, 형태소 분석, 사전적 의미, 본문 비평, 70인역 용례, 수사학적 기능, 상호본문성, 주요 해석사 등 총 14개 항목에 걸쳐 구절을 단어별로 상세히 분석합니다.
- **병렬 번역 대조**: 주요 번역본(NRSV, Schlachter 2000, 개역개정)을 원어 단어와 정확히 정렬하여, 번역이 원문의 어떤 단어에 해당하는지 직관적으로 보여줍니다.
- **자동 파일 생성**: 분석 결과를 `[책이름] [장]장 [절]절 주해.md` 형식의 파일 이름으로 자동 저장하여 체계적인 자료 관리를 돕습니다.
- **학술 표준 준수**: BHS(구약), NA28(신약) 등 학계 표준 비평 본문을 기반으로 분석을 수행합니다.

---

## 사용 방법 (Usage)

다양한 환경에서 이 프롬프트를 사용하는 방법입니다.

### 👉 가장 쉬운 방법 (AI 채팅 환경)

1.  AI 채팅창에 이 프롬프트 파일(`Bible_Analyze.md`)을 첨부합니다.
2.  그 다음, 분석하고 싶은 성경 구절을 입력합니다.

    **예시:**
    ```
    @Agent/bible/Bible_Analyze.md 히 12:2 주해해줘
    ```

### 👉 CLI 환경

1.  이 프롬프트 파일(`Bible_Analyze.md`)을 참조하는 CLI 명령어를 생성합니다.
2.  생성한 명령어를 사용하여 분석을 실행합니다.

    **예시:**
    ```bash
    gemini-cli bible-analyze "John 3:16"
    ```

### 👉 옵시디언(Obsidian) + CLI 연동 환경

사용하는 CLI 도구의 명령어 인식 기능에 따라 두 가지 방법으로 사용할 수 있습니다.

-   **명령어 인식이 가능한 경우:**
    슬래시(`/`)로 명령어를 호출한 후, 분석할 구절을 인자로 전달합니다.
    ```
    /bible:analyze "John 3:16"
    ```

-   **명령어 인식이 불가능한 경우:**
    1.  **(꼼수)** '가장 쉬운 방법'과 동일하게, 채팅창에 프롬프트 파일을 첨부하고 분석할 구절을 입력합니다.
    2.  **(자연어)** 또는, 프롬프트 내용을 옵시디언 노트로 만들어두고, 다음과 같이 자연어로 요청합니다.
        ```
        "'@Agent/bible/Bible_Analyze.md' 지침에 따라 '창세기 1:1'을 분석해줘"
        ```

### ✨ 팁: 원하는 언어로 분석하기

기본 설정은 한국어 중심이지만, 다음과 같이 요청하여 모든 분석 결과(컬럼 제목, 내용 등)를 사용자가 원하는 언어로 생성할 수 있습니다. 모델이 익숙한 언어라면 더욱 정확한 결과를 얻을 수 있습니다.

**예시:**
```
@Agent/bible/Bible_Analyze.md "John 1:1을 독일어로 주해해줘"
@Agent/bible/Bible_Analyze.md "요한복음 1:1을 일본어로 주해해줘"
```

---

## 결과물 예시 (요한복음 1:1)

| Verse | Original Text (BHS/NA28) | 음역 (Transliteration) | Parsing (형태소 분석) | Lemma (기본형) | Lexicon (핵심 의미) | Textual Notes (본문 비평) | LXX Usage (70인역 용례) | Rhetorical Function (수사학적 기능) | Intertextuality (상호본문성) | 주요 해석사 (Wirkungsgeschichte) | NRSV | Schlachter (2000) | 개역개정 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1:1a | Ἐν | 엔 | 전치사 | ἐν | ~안에, ~중에 | 본문이 안정적임 | 창 1:1의 בְּרֵאשִׁית 번역 | 절의 시작을 알리는 전치사구 | 창 1:1 시작과 동일한 표현 | | In | Im | 태초에 |
| 1:1a | ἀρχῇ | 아르케 | 명사, 여격, 단수, 여성 | ἀρχή | 시작, 근원 | 본문이 안정적임 | 잠 8:22-23에서 חכמה(지혜)의 시작을 묘사 | '말씀'의 시간적 기원을 정의 | 잠 8:22-31 (지혜 찬가) 암시 | | the beginning | Anfang | |
| 1:1b | ἦν | 엔 | 동사, 미완료, 직설법, 능동태, 3인칭, 단수 | εἰμί | ~이다, 존재하다 | 본문이 안정적임 | 출 3:14(אֶהְיֶה)와 연결, 존재 자체를 나타냄 | '말씀'의 계속적, 영원한 존재를 강조 | | | was | war | 계시니라 |
| 1:1c | καὶ | 카이 | 접속사 | καί | 그리고, 또한 | 본문이 안정적임 | | 세 개의 핵심 절을 연결하는 역할 | | | and | und | |
| 1:1d | ὁ | 호 | 관사, 주격, 단수, 남성 | ὁ | 그 | 본문이 안정적임 | | '말씀'을 특정하고 인격화함 | | | the | das | 이 |
| 1:1e | λόγος | 로고스 | 명사, 주격, 단수, 남성 | λόγος | 말씀, 진술, 메시지 | 관사 'ὁ'가 파피루스 66호 (𝔓⁶⁶) 등에서 생략됨. 그러나 시내 사본 (א), 바티칸 사본 (B) 등이 포함하여 NA28이 채택함. {확신도: A} | 시 33:6(דבר) 등에서 하나님의 창조적 말씀을 지칭 | 시의 주어이자 중심 개념 | 시 33:6, 잠 8장 | **이레니우스:** 성자의 성육신을 예표하는 내재적 로고스<br>**아우구스티누스:** 성부와 동일본질인 내적 말씀 | Word | Wort | 말씀이 |
| 1:1f | ἦν | 엔 | 동사, 미완료, 직설법, 능동태, 3인칭, 단수 | εἰμί | ~이다, 존재하다 | 본문이 안정적임 | | '말씀'의 존재 상태를 반복하여 강조 | | | | war | |
| 1:1g | πρὸς | 프로스 | 전치사 (대격 지배) | πρός | ~와 함께 | 본문이 안정적임 | | '말씀'과 '하나님'의 인격적 구별과 친밀한 관계를 동시에 표현 | | | with | bei | 함께 |
| 1:1h | τὸν | 톤 | 관사, 대격, 단수, 남성 | ὁ | 그 | 본문이 안정적임 | | | | | | Gott | 하나님과 |
| 1:1i | θεόν | 데온 | 명사, 대격, 단수, 남성 | θεός | 하나님 | 본문이 안정적임 | | | | | God, | | 계셨으니 |
| 1:1j | καὶ | 카이 | 접속사 | καί | 그리고, 또한 | 본문이 안정적임 | | | | | and | und | 이 말씀은 |
| 1:1k | θεὸς | 데오스 | 명사, 주격, 단수, 남성 | θεός | 하나님 | 관사 없는 'θεὸς'는 '말씀'의 신적 본질을 나타냄. | | 술어 주격(Predicate Nominative)으로, '말씀'의 신성을 정의함. | | **오리게네스:** 관사가 없으므로 성부보다 열등한 '신적 존재'로 해석.<br>**아타나시우스:** 성부와 동일한 신적 본질을 가지나, 인격적으로는 구별됨을 나타낸다고 반박. | | das Wort | 곧 |
| 1:1l | ἦν | 엔 | 동사, 미완료, 직설법, 능동태, 3인칭, 단수 | εἰμί | ~이다, 존재하다 | 본문이 안정적임 | | | | | | war | 하나님이시니라 |
| 1:1m | ὁ | 호 | 관사, 주격, 단수, 남성 | ὁ | 그 | 본문이 안정적임 | | | | | the | Gott. | | |
| 1:1n | λόγος | 로고스 | 명사, 주격, 단수, 남성 | λόγος | 말씀, 진술, 메시지 | 본문이 안정적임 | | | | | Word | | | |

## 분석 항목 설명

| 항목 (Column) | 내용 |
| :--- | :--- |
| **Verse** | 절 번호 |
| **Original Text (BHS/NA28)** | 원어 본문 (구약: BHS, 신약: NA28) |
| **음역 (Transliteration)** | 원어의 한국어 음역 |
| **Parsing (형태소 분석)** | 품사, 시제, 격, 성, 수 등 문법적 정보 |
| **Lemma (기본형)** | 단어의 사전 등재형 |
| **Lexicon (핵심 의미)** | 표준 원어 사전(BDAG, HALOT 등)에 기반한 핵심 의미 |
| **Textual Notes (본문 비평)** | 주요 사본들의 이문(異文) 정보 및 본문 채택 근거 |
| **LXX Usage (70인역 용례)** | 70인역(Septuagint)에서 해당 단어가 사용된 용례 |
| **Rhetorical Function (수사학적 기능)** | 문맥 안에서 단어가 수행하는 수사학적 역할 |
| **Intertextuality (상호본문성)** | 다른 성경 본문과의 인용 또는 암시 관계 |
| **주요 해석사 (Wirkungsgeschichte)** | 역사적으로 중요한 신학자나 교부의 해석 요약 |
| **NRSV** | New Revised Standard Version 번역 대조 |
| **Schlachter (2000)** | 독일어 Schlachter 2000 성경 번역 대조 |
| **개역개정** | 한국어 개역개정 성경 번역 대조 |

---

## ⚠️ 주의사항 (Disclaimer)

이 AI 어시스턴트가 생성하는 내용은 학술적 연구를 보조하기 위한 자료이며, 오류를 포함하고 있을 수 있습니다. 모든 분석 결과(특히 본문 비평, 해석사, 용례 등)는 반드시 공인된 학술 자료를 통해 재차 확인하고 검증하는 과정이 필요합니다.

## 📜 저작권 및 라이선스 (Copyright & License)

이 프롬프트는 [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/)에 따라 라이선스가 부여됩니다. 개인적인 학습 및 비상업적 연구 목적으로 자유롭게 사용, 수정, 배포할 수 있으나, 상업적 이용은 금지됩니다.

---

# English Version

## Biblical Exegesis Assistant Prompt

This repository contains a prompt designed to configure a Large Language Model (LLM) like Gemini to function as a specialized "Biblical Exegesis Assistant." This prompt instructs the model to perform a deep, scholarly analysis of a given biblical verse and format the output into a systematic Markdown table.

## Features

- **Multi-faceted Analysis**: Conducts a detailed, word-by-word analysis of a verse across 14 distinct categories.
- **Parallel Translation Alignment**: Precisely aligns major translations (NRSV, Schlachter 2000, Korean 개역개정) with the corresponding word in the original text.
- **Automatic File Generation**: Automatically saves the analysis to a Markdown file.
- **Adherence to Academic Standards**: Performs analysis based on standard critical editions (BHS for OT, NA28 for NT).

---

## How to Use

Here are several ways to use this prompt in different environments.

### 👉 Easiest Method (in an AI Chat Interface)

1.  Attach this prompt file (`Bible_Analyze.md`) to the chat window.
2.  Then, simply type the biblical verse you want to analyze.

    **Example:**
    ```
    @Agent/bible/Bible_Analyze.md Analyze Hebrews 12:2 for me.
    ```

### 👉 In a CLI Environment

1.  Create a custom CLI command that references this prompt file (`Bible_Analyze.md`).
2.  Run the analysis using your custom command.

    **Example:**
    ```bash
    gemini-cli bible-analyze "John 3:16"
    ```

### 👉 In an Obsidian + CLI Integrated Environment

Your approach may differ depending on your specific tooling.

-   **If your CLI recognizes slash commands:**
    Invoke the command with a slash (`/`) and pass the verse as an argument.
    ```
    /bible:analyze "John 3:16"
    ```

-   **If your CLI does not recognize slash commands:**
    1.  **(Workaround)** Use the "Easiest Method" above by attaching the prompt file and typing the verse directly in the chat.
    2.  **(Natural Language)** Alternatively, reference the prompt as a note and make a natural language request.
        ```
        "Analyze 'Genesis 1:1' according to the instructions in '@Agent/bible/Bible_Analyze.md'"
        ```

### ✨ Tip: Generating Analysis in Your Preferred Language

While the prompt is configured for a Korean-centric output by default, you can request the entire analysis in any language familiar to the model. This will translate column headers and generate all descriptive content in your specified language, often with better accuracy if the model is proficient in that language.

**Examples:**
```
@Agent/bible/Bible_Analyze.md "Analyze John 1:1 in German"
@Agent/bible/Bible_Analyze.md "Analyze John 1:1 in Japanese"
```

---

## Example Output (for John 1:1)

| Verse | Original Text (BHS/NA28) | Transliteration | Parsing | Lemma | Lexicon | Textual Notes | LXX Usage | Rhetorical Function | Intertextuality | History of Interpretation (Wirkungsgeschichte) | NRSV | Schlachter (2000) | NKRV (Korean) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1:1a | Ἐν | En | Preposition | ἐν | in, among, with | The text is stable. | Translates בְּרֵאשִׁית (bereshith) in Gen 1:1. | The prepositional phrase establishes the temporal setting for the entire prologue. | Directly alludes to the opening of Gen 1:1. | | In | Im | 태초에 |
| 1:1a | ἀρχῇ | archē | Noun, Dative, Sg, Fem | ἀρχή | beginning, origin, ruler | The text is stable. | Used to describe the beginning of Wisdom (חכמה) in Prov 8:22-23. | Defines the temporal origin of the Logos, placing him before creation. | Alludes to the Wisdom hymn in Prov 8:22-31. | | the beginning | Anfang | |
| 1:1b | ἦν | ēn | Verb, Impf, Ind, Act, 3rd, Sg | εἰμί | to be, exist | The text is stable. | Linked to the divine name in Ex 3:14 (LXX: ἐγώ εἰμι ὁ ὤν), indicating eternal existence. | The imperfect tense emphasizes the continuous, timeless existence of the Logos. | | | was | war | 계시니라 |
| 1:1c | καὶ | kai | Conjunction | καί | and, also | The text is stable. | | Functions as a coordinating conjunction, linking the three foundational clauses of the verse. | | | and | und | |
| 1:1d | ὁ | ho | Article, Nom, Sg, Masc | ὁ | the | The text is stable. | | Specifies and personifies the Logos. | | | the | das | 이 |
| 1:1e | λόγος | logos | Noun, Nom, Sg, Masc | λόγος | word, statement, reason | The article 'ὁ' is omitted in some manuscripts like Papyrus 66 (𝔓⁶⁶), but included in major witnesses like Codex Sinaiticus (א) and Codex Vaticanus (B). NA28 adopts the reading with the article. {Confidence: A} | Refers to the creative word of God (דבר, davar) in passages like Ps 33:6. | The central subject of the prologue. | Ps 33:6, Prov 8. | **Irenaeus:** The immanent Logos, prefiguring the incarnation of the Son.<br>**Augustine:** The internal Word, consubstantial with the Father. | Word | Wort | 말씀이 |
| 1:1f | ἦν | ēn | Verb, Impf, Ind, Act, 3rd, Sg | εἰμί | to be, exist | The text is stable. | | Repeats the verb to emphasize the state of being of the Logos. | | | | war | |
| 1:1g | πρὸς | pros | Preposition (with Acc) | πρός | with, toward, to | The text is stable. | | Expresses both personal distinction and intimate communion between the Logos and God. | | | with | bei | 함께 |
| 1:1h | τὸν | ton | Article, Acc, Sg, Masc | ὁ | the | The text is stable. | | | | | | Gott | 하나님과 |
| 1:1i | θεόν | theon | Noun, Acc, Sg, Masc | θεός | God | The text is stable. | | | | | God, | | 계셨으니 |
| 1:1j | καὶ | kai | Conjunction | καί | and, also | The text is stable. | | | | | and | und | 이 말씀은 |
| 1:1k | θεὸς | theos | Noun, Nom, Sg, Masc | θεός | God, a god | The anarthrous (no article) 'θεὸς' serves as a predicate nominative, indicating the divine nature of the Logos, not identity with 'τὸν θεόν' (the Father). | | Defines the nature of the Logos as divine. | | **Origen:** Interpreted the lack of an article to mean a lesser, secondary divinity.<br>**Athanasius:** Argued it signifies shared divine essence while maintaining personal distinction from the Father. | | das Wort | 곧 |
| 1:1l | ἦν | ēn | Verb, Impf, Ind, Act, 3rd, Sg | εἰμί | to be, exist | The text is stable. | | The third use of 'ἦν' brings the opening statement to a climactic conclusion. | | | | war | 하나님이시니라 |
| 1:1m | ὁ | ho | Article, Nom, Sg, Masc | ὁ | the | The text is stable. | | | | | the | Gott. | | |
| 1:1n | λόγος | logos | Noun, Nom, Sg, Masc | λόγος | word, statement, reason | The text is stable. | | Repeats the subject for rhetorical emphasis and closure. | | | Word | | | |

## Column Descriptions

| Column | Description |
| :--- | :--- |
| **Verse** | The verse number. |
| **Original Text (BHS/NA28)** | The original text from the critical edition. |
| **음역 (Transliteration)** | A Korean transliteration of the original text. |
| **Parsing (형태소 분석)** | Grammatical information (part of speech, tense, case, etc.). |
| **Lemma (기본형)** | The word's dictionary lookup form. |
| **Lexicon (핵심 의미)** | The core meaning based on standard lexicons (e.g., BDAG, HALOT). |
| **Textual Notes (본문 비평)** | Information on significant manuscript variants. |
| **LXX Usage (70인역 용례)** | Examples of the word's use in the Septuagint. |
| **Rhetorical Function (수사학적 기능)** | The word's rhetorical role in its context. |
| **Intertextuality (상호본문성)** | Allusions to or quotations of other biblical texts. |
| **주요 해석사 (Wirkungsgeschichte)** | A summary of the word's interpretation by major historical theologians. |
| **NRSV** | A parallel alignment with the New Revised Standard Version. |
| **Schlachter (2000)** | A parallel alignment with the German Schlachter 2000 Bible. |
| **개역개정** | A parallel alignment with the Korean New Korean Revised Version. |

---

## ⚠️ Disclaimer

The content generated by this AI assistant is intended to supplement scholarly research and may contain errors. All analytical results, especially those concerning textual criticism, historical interpretation, and usage examples, must be cross-verified with established academic sources.

## 📜 Copyright & License

This prompt is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/). You are free to use, modify, and distribute it for personal, educational, and non-commercial research purposes. Commercial use is strictly prohibited.