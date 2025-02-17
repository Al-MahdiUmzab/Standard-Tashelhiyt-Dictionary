# Standard-Tashelhiyt-Dictionary
A comprehensive dictionary of Tashelhiyt Language
<!DOCTYPE html>
<html>
<head>
    <title>Tachelhit Dictionary | قاموس تشلحيت</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta charset="UTF-8">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f0f2f5;
        }

        .header {
            text-align: center;
            margin-bottom: 20px;
        }

        .language-toggle {
            text-align: center;
            margin-bottom: 20px;
        }

        .btn-toggle {
            background-color: #3182ce;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 4px;
            cursor: pointer;
            margin: 0 5px;
        }

        .btn-toggle.active {
            background-color: #2c5282;
        }

        .search-container {
            max-width: 800px;
            margin: 0 auto;
            margin-bottom: 20px;
        }

        #searchInput {
            width: 100%;
            padding: 12px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .word-list {
            max-width: 800px;
            margin: 0 auto;
        }

        .word-card {
            background: white;
            padding: 20px;
            margin-bottom: 15px;
            border-radius: 8px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        .word-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 15px;
        }

        .word-main-info {
            display: flex;
            flex-direction: column;
        }

        .tachelhit {
            font-weight: bold;
            color: #2c5282;
            font-size: 24px;
        }

        .arabic-tifinagh {
            display: flex;
            flex-direction: column;
            align-items: flex-end;
        }

        .arabic {
            font-size: 24px;
            color: #4a5568;
            font-family: 'Traditional Arabic', Arial, sans-serif;
        }

        .tifinagh {
            font-size: 20px;
            color: #4a5568;
            font-family: 'Noto Sans Tifinagh', Arial, sans-serif;
            margin-top: 5px;
        }

        .pos {
            display: inline-block;
            padding: 3px 8px;
            background-color: #e2e8f0;
            border-radius: 4px;
            font-size: 14px;
            color: #4a5568;
            margin-top: 5px;
        }

        .forms-variants {
            margin: 10px 0;
            padding: 5px 0;
            border-top: 1px solid #edf2f7;
            border-bottom: 1px solid #edf2f7;
            color: #4a5568;
            font-size: 15px;
        }

        .section {
            margin: 12px 0;
            padding: 8px 0;
            border-bottom: 1px solid #edf2f7;
        }

        .section-title {
            font-weight: bold;
            color: #4a5568;
            font-size: 14px;
            text-transform: uppercase;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
        }

        .section-title.collapsible {
            cursor: pointer;
        }

        .section-title.collapsible:hover {
            color: #2c5282;
        }

        .section-content {
            color: #4a5568;
            font-size: 16px;
        }

        .definition {
            font-size: 16px;
        }

        .hidden-content {
            display: none;
        }

        .example {
            color: #718096;
            font-style: italic;
            margin-top: 5px;
            font-size: 14px;
            padding-bottom: 5px;
        }

        .etymology {
            background-color: #f7fafc;
            padding: 10px;
            border-radius: 4px;
            margin-top: 10px;
            font-size: 14px;
            color: #666;
        }

        .audio-btn {
            background-color: #3182ce;
            color: white;
            border: none;
            border-radius: 50%;
            width: 32px;
            height: 32px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            margin-left: 10px;
        }

        .audio-btn:hover {
            background-color: #2c5282;
        }

        .conjugation-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }

        .conjugation-table th, .conjugation-table td {
            border: 1px solid #e2e8f0;
            padding: 8px;
            text-align: center;
        }

        .conjugation-table th {
            background-color: #f7fafc;
            font-weight: normal;
        }

        .chevron {
            transition: transform 0.3s;
        }

        .chevron.down {
            transform: rotate(180deg);
        }

        [dir="rtl"] .word-header {
            flex-direction: row-reverse;
        }

        [dir="rtl"] .section-title {
            flex-direction: row-reverse;
        }

        .more-examples-btn {
            background: none;
            border: none;
            color: #3182ce;
            cursor: pointer;
            padding: 5px 0;
            font-size: 14px;
            display: flex;
            align-items: center;
        }

        .more-examples-btn:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1 id="pageTitle">Tachelhit Dictionary</h1>
    </div>

    <div class="language-toggle">
        <button id="enBtn" class="btn-toggle active">English</button>
        <button id="arBtn" class="btn-toggle">العربية</button>
    </div>

    <div class="search-container">
        <input type="text" id="searchInput" placeholder="Search for a word...">
    </div>

    <div class="word-list" id="wordList">
        <!-- Words will be added here -->
    </div>

    <script>
        const dictionary = [
            {
                tachelhit: "afus",
                arabic: "أفوس",
                tifinagh: "ⴰⴼⵓⵙ",
                partOfSpeech: {
                    en: "noun",
                    ar: "اسم"
                },
                plural: "ifassn",
                pluralArabic: "إفاسّن",
                definition: {
                    en: "hand",
                    ar: "يد"
                },
                examples: [
                    {
                        en: "ifka yas ufus nns - He gave him his hand",
                        ar: "إفكا ياس أوفوس نّس - أعطاه يده"
                    },
                    {
                        en: "ishd ufus nns - His hand is strong",
                        ar: "إشدّ أوفوس نّس - يده قوية"
                    }
                ],
                etymology: {
                    en: "From Proto-Berber *a-fus (hand)",
                    ar: "من البربرية الأم *a-fus (يد)"
                },
                variants: "ufus (construct state)"
            },
            {
                tachelhit: "ili",
                arabic: "إلي",
                tifinagh: "ⵉⵍⵉ",
                partOfSpeech: {
                    en: "verb",
                    ar: "فعل"
                },
                definition: {
                    en: "to be, to exist",
                    ar: "يكون، يوجد"
                },
                examples: [
                    {
                        en: "illa ɣ tgmmi - He is at home",
                        ar: "إلّا غ تݣمّي - هو في البيت"
                    },
                    {
                        en: "ur illi ma s nit izwarn - There is no one who surpasses him",
                        ar: "أور إلّي ما س نيت إزوارن - لا يوجد من يتفوق عليه"
                    }
                ],
                etymology: {
                    en: "From Proto-Berber *ili (to be)",
                    ar: "من البربرية الأم *ili (يكون)"
                },
                conjugation: {
                    present: {
                        "1s": "lliɣ",
                        "2s.m": "tllit",
                        "2s.f": "tllit",
                        "3s.m": "illa",
                        "3s.f": "tlla",
                        "1p": "nlla",
                        "2p": "tllam",
                        "3p": "llan"
                    },
                    past: {
                        "1s": "lliɣ",
                        "2s.m": "tllit",
                        "2s.f": "tllit",
                        "3s.m": "illa",
                        "3s.f": "tlla",
                        "1p": "nlla",
                        "2p": "tllam",
                        "3p": "llan"
                    },
                    future: {
                        "1s": "rad iliɣ",
                        "2s.m": "rad tilit",
                        "2s.f": "rad tilit",
                        "3s.m": "rad ili",
                        "3s.f": "rad tili",
                        "1p": "rad nili",
                        "2p": "rad tilim",
                        "3p": "rad ilin"
                    }
                },
                variants: "ili (infinitive)"
            },
            {
                tachelhit: "amllal",
                arabic: "أملّال",
                tifinagh: "ⴰⵎⵍⵍⴰⵍ",
                partOfSpeech: {
                    en: "adjective",
                    ar: "صفة"
                },
                plural: "imllalen",
                pluralArabic: "إملّالن",
                definition: {
                    en: "white",
                    ar: "أبيض"
                },
                examples: [
                    {
                        en: "aḥruy amllal - white cloth",
                        ar: "أحروي أملّال - قماش أبيض"
                    },
                    {
                        en: "tamllalt n tglay - the white of the egg",
                        ar: "تاملّالت ن تݣلاي - بياض البيضة"
                    }
                ],
                etymology: {
                    en: "From Proto-Berber *mellul (white)",
                    ar: "من البربرية الأم *mellul (أبيض)"
                },
                variants: "feminine: tamllalt, plural feminine: timllalen"
            }
            // Add more words here
        ];

        // Language state
        let currentLang = 'en';

        // Toggle language function
        function toggleLanguage(lang) {
            currentLang = lang;
            
            // Update UI elements
            if (lang === 'ar') {
                document.body.setAttribute('dir', 'rtl');
                document.getElementById('pageTitle').innerText = 'قاموس تشلحيت';
                document.getElementById('searchInput').placeholder = 'ابحث عن كلمة...';
                document.getElementById('arBtn').classList.add('active');
                document.getElementById('enBtn').classList.remove('active');
            } else {
                document.body.setAttribute('dir', 'ltr');
                document.getElementById('pageTitle').innerText = 'Tachelhit Dictionary';
                document.getElementById('searchInput').placeholder = 'Search for a word...';
                document.getElementById('enBtn').classList.add('active');
                document.getElementById('arBtn').classList.remove('active');
            }
            
            // Redisplay the words with the current language
            displayWords(filterWords(document.getElementById('searchInput').value));
        }

        // Add event listeners for language toggle buttons
        document.getElementById('enBtn').addEventListener('click', () => toggleLanguage('en'));
        document.getElementById('arBtn').addEventListener('click', () => toggleLanguage('ar'));

        // Function to filter words based on search input
        function filterWords(searchTerm) {
            searchTerm = searchTerm.toLowerCase();
            
            return dictionary.filter(word => 
                word.tachelhit.toLowerCase().includes(searchTerm) ||
                word.arabic.includes(searchTerm) ||
                word.definition[currentLang].toLowerCase().includes(searchTerm) ||
                (word.plural && word.plural.toLowerCase().includes(searchTerm)) ||
                (word.tifinagh && word.tifinagh.includes(searchTerm))
            );
        }

        // Function to toggle collapsible sections
        function toggleSection(element) {
            const content = element.nextElementSibling;
            const chevron = element.querySelector('.chevron');
            
            if (content.style.display === 'block') {
                content.style.display = 'none';
                chevron.classList.remove('down');
            } else {
                content.style.display = 'block';
                chevron.classList.add('down');
            }
        }

        // Function to toggle more examples
        function toggleMoreExamples(btn) {
            const moreExamples = btn.nextElementSibling;
            const showText = currentLang === 'en' ? 'Show more examples' : 'عرض المزيد من الأمثلة';
            const hideText = currentLang === 'en' ? 'Hide examples' : 'إخفاء الأمثلة';
            
            if (moreExamples.style.display === 'block') {
                moreExamples.style.display = 'none';
                btn.innerHTML = `${showText} <span class="chevron">▼</span>`;
            } else {
                moreExamples.style.display = 'block';
                btn.innerHTML = `${hideText} <span class="chevron down">▼</span>`;
            }
        }

        // Function to display words
        function displayWords(words) {
            const wordList = document.getElementById('wordList');
            wordList.innerHTML = '';

            const showMoreText = currentLang === 'en' ? 'Show more examples' : 'عرض المزيد من الأمثلة';

            words.forEach(word => {
                const wordCard = document.createElement('div');
                wordCard.className = 'word-card';
                
                // Forms and variants section (now at the top, not collapsible)
                let formsVariantsContent = '';
                if (word.plural || word.variants) {
                    let variantContent = [];
                    if (word.plural) {
                        variantContent.push(`${currentLang === 'en' ? 'Plural' : 'الجمع'}: ${word.plural} ${word.pluralArabic ? `(${word.pluralArabic})` : ''}`);
                    }
                    if (word.variants) {
                        variantContent.push(word.variants);
                    }
                    formsVariantsContent = `
                        <div class="forms-variants">
                            ${variantContent.join(' | ')}
                        </div>
                    `;
                }

                // Examples section (first example visible, rest hidden)
                let examplesSection = '';
                if (word.examples && word.examples.length > 0) {
                    // First example always visible
                    let firstExample = `<div class="example">${word.examples[0][currentLang]}</div>`;
                    
                    // Additional examples (if any) hidden initially
                    let moreExamples = '';
                    if (word.examples.length > 1) {
                        moreExamples = `
                            <button class="more-examples-btn" onclick="toggleMoreExamples(this)">
                                ${showMoreText} <span class="chevron">▼</span>
                            </button>
                            <div class="hidden-content">
                                ${word.examples.slice(1).map(ex => 
                                    `<div class="example">${ex[currentLang]}</div>`
                                ).join('')}
                            </div>
                        `;
                    }
                    
                    examplesSection = `
                        <div class="section">
                            <div class="section-title">
                                ${currentLang === 'en' ? 'EXAMPLES' : 'أمثلة'}
                            </div>
                            ${firstExample}
                            ${moreExamples}
                        </div>
                    `;
                }

                // Conjugation section for verbs
                let conjugationSection = '';
                if (word.partOfSpeech[currentLang] === (currentLang === 'en' ? 'verb' : 'فعل') && word.conjugation) {
                    const presentLabel = currentLang === 'en' ? 'Present' : 'المضارع';
                    const pastLabel = currentLang === 'en' ? 'Past' : 'الماضي';
                    const futureLabel = currentLang === 'en' ? 'Future' : 'المستقبل';
                    
                    conjugationSection = `
                        <div class="section">
                            <div class="section-title collapsible" onclick="toggleSection(this)">
                                ${currentLang === 'en' ? 'CONJUGATION' : 'التصريف'}
                                <span class="chevron">▼</span>
                            </div>
                            <div class="hidden-content">
                                <table class="conjugation-table">
                                    <thead>
                                        <tr>
                                            <th>${currentLang === 'en' ? 'Person' : 'الضمير'}</th>
                                            <th>${presentLabel}</th>
                                            <th>${pastLabel}</th>
                                            <th>${futureLabel}</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>${currentLang === 'en' ? '1st sing.' : 'المتكلم المفرد'}</td>
                                            <td>${word.conjugation.present["1s"]}</td>
                                            <td>${word.conjugation.past["1s"]}</td>
                                            <td>${word.conjugation.future["1s"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '2nd sing. (m)' : 'المخاطب المفرد'}</td>
                                            <td>${word.conjugation.present["2s.m"]}</td>
                                            <td>${word.conjugation.past["2s.m"]}</td>
                                            <td>${word.conjugation.future["2s.m"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '2nd sing. (f)' : 'المخاطبة المفردة'}</td>
                                            <td>${word.conjugation.present["2s.f"]}</td>
                                            <td>${word.conjugation.past["2s.f"]}</td>
                                            <td>${word.conjugation.future["2s.f"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '3rd sing. (m)' : 'الغائب المفرد'}</td>
                                            <td>${word.conjugation.present["3s.m"]}</td>
                                            <td>${word.conjugation.past["3s.m"]}</td>
                                            <td>${word.conjugation.future["3s.m"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '3rd sing. (f)' : 'الغائبة المفردة'}</td>
                                            <td>${word.conjugation.present["3s.f"]}</td>
                                            <td>${word.conjugation.past["3s.f"]}</td>
                                            <td>${word.conjugation.future["3s.f"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '1st plur.' : 'المتكلمون الجمع'}</td>
                                            <td>${word.conjugation.present["1p"]}</td>
                                            <td>${word.conjugation.past["1p"]}</td>
                                            <td>${word.conjugation.future["1p"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '2nd plur.' : 'المخاطبون الجمع'}</td>
                                            <td>${word.conjugation.present["2p"]}</td>
                                            <td>${word.conjugation.past["2p"]}</td>
                                            <td>${word.conjugation.future["2p"]}</td>
                                        </tr>
                                        <tr>
                                            <td>${currentLang === 'en' ? '3rd plur.' : 'الغائبون الجمع'}</td>
                                            <td>${word.conjugation.present["3p"]}</td>
                                            <td>${word.conjugation.past["3p"]}</td>
                                            <td>${word.conjugation.future["3p"]}</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    `;
                }

                wordCard.innerHTML = `
                    <div class="word-header">
                        <div class="word-main-info">
                            <div class="tachelhit">${word.tachelhit}</div>
                            <div class="pos">${word.partOfSpeech[currentLang]}</div>
                        </div>
                        <div class="arabic-tifinagh">
                            <div class="arabic">${word.arabic}</div>
                            <div class="tifinagh">${word.tifinagh}</div>
                        </div>
                    </div>
                    
                    ${formsVariantsContent}

                    <div class="section">
                        <div class="section-title collapsible" onclick="toggleSection(this)">
                            ${currentLang === 'en' ? 'ETYMOLOGY' : 'أصل الكلمة'}
                            <span class="chevron">▼</span>
                        </div>
                        <div class="hidden-content etymology">
                            ${word.etymology[currentLang]}
                        </div>
                    </div>

                    <div class="section">
                        <div class="section-title">
                            ${currentLang === 'en' ? 'DEFINITION' : 'المعنى'}
                            <button class="audio-btn" title="${currentLang === 'en' ? 'Listen to pronunciation' : 'استمع إلى النطق'}">
                                ▶
                            </button>
                        </div>
                        <div class="section-content definition">
                            ${word.definition[currentLang]}
                        </div>
                    </div>

                    ${examplesSection}
                    ${conjugationSection}
                `;
                
                wordList.appendChild(wordCard);
                
                // Add event listener for audio button
                const audioBtn = wordCard.querySelector('.audio-btn');
                audioBtn.addEventListener('click', () => {
                    alert(`${currentLang === 'en' ? 'Audio for' : 'الصوت ل'} "${word.tachelhit}" ${currentLang === 'en' ? 'would play here' : 'سيُشغل هنا'}`);
                });
            });
        }

        // Add event listener for search
        document.getElementById('searchInput').addEventListener('input', function(e) {
            const filteredWords = filterWords(e.target.value);
            displayWords(filteredWords);
        });

        // Initial display
        displayWords(dictionary);
    </script>
</body>
</html>
