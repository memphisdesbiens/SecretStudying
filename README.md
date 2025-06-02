<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>School Subjects Portal</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            margin: 0;
            padding: 0;
            min-height: 100vh;
            background: linear-gradient(135deg, #ffe600 0%, #000 100%);
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            background-attachment: fixed;
        }
        header {
            background: #2d3e50;
            color: #fff;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 30px;
            height: 70px;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        nav {
            display: flex;
            gap: 25px;
        }
        nav a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            font-size: 1.1em;
            transition: color 0.2s;
        }
        nav a:hover {
            color: #ffd700;
        }
        #clock {
            font-size: 1.1em;
            letter-spacing: 1px;
            font-family: 'Courier New', Courier, monospace;
        }
        main {
            max-width: 900px;
            margin: 40px auto;
            padding: 0 20px;
        }
        section {
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.07);
            margin-bottom: 40px;
            padding: 32px 28px;
        }
        section h2 {
            margin-top: 0;
            color: #2d3e50;
            border-bottom: 2px solid #e0e4ea;
            padding-bottom: 8px;
        }
        #est-clock-bg {
            position: fixed;
            top: 30px;
            right: 40px;
            z-index: 20;
            font-size: 2.2em;
            color: #2d3e50;
            background: rgba(255,255,255,0.7);
            border-radius: 12px;
            padding: 8px 22px;
            font-family: 'Segoe UI', Arial, sans-serif;
            box-shadow: 0 2px 12px #0002;
            letter-spacing: 2px;
        }
        @media (max-width: 600px) {
            header {
                flex-direction: column;
                align-items: flex-start;
                height: auto;
                padding: 15px;
            }
            nav {
                margin-top: 10px;
                gap: 15px;
            }
            main {
                padding: 0 5px;
            }
            section {
                padding: 18px 8px;
            }
        }
        #ai-character-container {
  position: fixed;
  bottom: 30px;
  right: 30px;
  z-index: 9999 !important;
  display: flex;
  flex-direction: column;
  align-items: center;
}
#ai-character-head {
  width: 110px;
  height: 110px;
  background: #ffe600;
  border: 4px solid #222;
  border-radius: 50%;
  position: relative;
  box-shadow: 0 4px 24px #0004;
  animation: head-bob 2.5s infinite ease-in-out;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #fff;
}
#ai-character-head-inner {
  width: 100px;
  height: 100px;
  background: #ffe600;
  border-radius: 50%;
  position: relative;
}
@keyframes head-bob {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}
.ai-eye {
  position: absolute;
  width: 18px;
  height: 18px;
  background: #222;
  border-radius: 50%;
  top: 38px;
  left: 28px;
  box-shadow: 36px 0 0 0 #222;
  animation: blink 4s infinite;
}
@keyframes blink {
  0%, 92%, 100% { height: 18px; }
  95% { height: 3px; }
}
.ai-mouth {
  position: absolute;
  width: 38px;
  height: 18px;
  left: 36px;
  top: 70px;
  border-bottom: 4px solid #222;
  border-radius: 0 0 38px 38px;
  animation: mouth-talk 2.5s infinite;
}
@keyframes mouth-talk {
  0%, 100% { height: 18px; }
  20% { height: 24px; }
  40% { height: 10px; }
  60% { height: 18px; }
  80% { height: 22px; }
}
#ai-chat-box {
  margin-top: 10px;
  background: #fffbe6;
  border: 2px solid #ffe600;
  border-radius: 12px;
  padding: 10px 14px;
  min-width: 260px;
  max-width: 340px;
  font-size: 1em;
  color: #222;
  box-shadow: 0 2px 12px #0002;
  opacity: 0;
  transform: translateY(20px) scale(0.98);
  pointer-events: none;
  transition: opacity 0.35s cubic-bezier(.4,2,.6,1), transform 0.35s cubic-bezier(.4,2,.6,1);
  position: relative;
  z-index: 10001;
}
#ai-character-head.ai-chat-open + #ai-chat-box,
#ai-chat-box.ai-chat-open {
  opacity: 1;
  transform: translateY(0) scale(1);
  pointer-events: auto;
}
        </style>
</head>
<body>
    <header>
        <nav>
            <a href="#math">Math</a>
            <a href="#english">English</a>
            <a href="#physical-science">Physical Science</a>
            <a href="#social-studies">Social/World Studies</a>
        </nav>
        <div id="clock"></div>
    </header>
    <main>
        <section id="math">
            <h2>Math</h2>
            <p>
                Math is the language of logic, patterns, and problem-solving. In high school, you will progress from foundational algebra and geometry to advanced topics like trigonometry, statistics, and calculus. Each grade deepens your understanding of mathematical concepts, real-world applications, and analytical thinking. Math classes help you develop skills for science, technology, engineering, finance, and everyday life.
            </p>
            <ul>
                <li>
                    Math:
                    <select onchange="showGradeTopics(this, 'math')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="math-topics" style="display:none;"></select>
                </li>
            </ul>
        </section>
        <section id="english">
            <h2>English</h2>
            <p>
                English Language Arts builds your reading, writing, speaking, and critical thinking skills. Each year, you will explore literature from different cultures and eras, analyze texts, write essays and research papers, and practice communication. English classes help you become a thoughtful reader, a clear writer, and an effective communicator in school and beyond.
            </p>
            <ul>
                <li>
                    English:
                    <select onchange="showGradeTopics(this, 'english')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="english-topics" style="display:none;"></select>
                </li>
            </ul>
        </section>
        <section id="physical-science">
            <h2>Physical Science</h2>
            <p>
                Physical Science explores the laws and properties of the non-living world. You will study physics, chemistry, astronomy, and earth science, learning about matter, energy, motion, forces, atoms, reactions, and the universe. Each grade introduces new scientific concepts, hands-on experiments, and real-world applications to build your scientific literacy and curiosity.
            </p>
            <ul>
                <li>
                    Physical Science:
                    <select onchange="showGradeTopics(this, 'physical-science')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="physical-science-topics" style="display:none;"></select>
                </li>
            </ul>
        </section>
        <section id="social-studies">
            <h2>Social/World Studies</h2>
            <p>
                Social Studies helps you understand people, societies, and the world. You will learn about history, geography, government, economics, and cultures. Each grade covers new eras, regions, and themes, teaching you how past events shape the present, how governments work, and how cultures interact. Social Studies classes prepare you to be an informed, responsible, and engaged citizen.
            </p>
            <ul>
                <li>
                    History:
                    <select onchange="showGradeTopics(this, 'history')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="history-topics" style="display:none;"></select>
                </li>
                <li>
                    Geography:
                    <select onchange="showGradeTopics(this, 'geography')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="geography-topics" style="display:none;"></select>
                </li>
                <li>
                    Civics:
                    <select onchange="showGradeTopics(this, 'civics')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="civics-topics" style="display:none;"></select>
                </li>
                <li>
                    World Cultures:
                    <select onchange="showGradeTopics(this, 'world-cultures')">
                        <option value="">Select Grade</option>
                        <option value="9">9th Grade</option>
                        <option value="10">10th Grade</option>
                        <option value="11">11th Grade</option>
                        <option value="12">12th Grade</option>
                    </select>
                    <select id="world-cultures-topics" style="display:none;"></select>
                </li>
            </ul>
        </section>
    </main>
    <section id="notes" style="margin-top:40px;">
        <h2>Class Notes by Subject & Grade</h2>
        <div style="display: flex; flex-wrap: wrap; gap: 32px;">
            <div style="flex:1; min-width:260px;">
                <h3>Math</h3>
                <ul>
                    <li><strong>9th Grade:</strong> <span id="notes-math-9">Algebra I, linear equations, and introductory geometry. Focus on foundational algebraic concepts, graphing, and problem-solving skills.</span></li>
                    <li><strong>10th Grade:</strong> <span id="notes-math-10">Geometry, proofs, and trigonometry. Emphasis on spatial reasoning, logical arguments, and properties of shapes and figures.</span></li>
                    <li><strong>11th Grade:</strong> <span id="notes-math-11">Algebra II, quadratic functions, statistics, and sequences. Develops advanced algebraic techniques and introduces probability and data analysis.</span></li>
                    <li><strong>12th Grade:</strong> <span id="notes-math-12">Pre-calculus and calculus. Covers limits, derivatives, integrals, and advanced mathematical modeling for college readiness.</span></li>
                </ul>
            </div>
            <div style="flex:1; min-width:260px;">
                <h3>English</h3>
                <ul>
                    <li><strong>9th Grade:</strong> <span id="notes-english-9">Introduction to literature, grammar, and writing. Study of short stories, novels, poetry, and basic essay composition.</span></li>
                    <li><strong>10th Grade:</strong> <span id="notes-english-10">World literature, research writing, and drama. Focus on analytical essays, persuasive writing, and public speaking.</span></li>
                    <li><strong>11th Grade:</strong> <span id="notes-english-11">American literature, critical analysis, and creative writing. Emphasis on nonfiction, literary criticism, and SAT/ACT preparation.</span></li>
                    <li><strong>12th Grade:</strong> <span id="notes-english-12">British literature, advanced composition, and college essays. Develops skills in literary analysis and academic writing.</span></li>
                </ul>
            </div>
            <div style="flex:1; min-width:260px;">
                <h3>Physical Science</h3>
                <ul>
                    <li><strong>9th Grade:</strong> <span id="notes-physical-science-9">Introduction to scientific methods, measurement, and basic chemistry and physics. Emphasizes lab safety and foundational science concepts.</span></li>
                    <li><strong>10th Grade:</strong> <span id="notes-physical-science-10">Chemistry, periodic table, and motion. Covers chemical reactions, forces, and energy transformations.</span></li>
                    <li><strong>11th Grade:</strong> <span id="notes-physical-science-11">Waves, electricity, magnetism, and astronomy. Explores sound, light, circuits, and the universe.</span></li>
                    <li><strong>12th Grade:</strong> <span id="notes-physical-science-12">Advanced physics, nuclear chemistry, and earth/space science. Focus on environmental science and scientific research projects.</span></li>
                </ul>
            </div>
            <div style="flex:1; min-width:260px;">
                <h3>Social/World Studies</h3>
                <ul>
                    <li><strong>History 9:</strong> <span id="notes-history-9">Ancient civilizations, world history, and the Middle Ages. Study of early societies, cultural developments, and major historical events.</span></li>
                    <li><strong>History 10:</strong> <span id="notes-history-10">Modern world history, revolutions, and industrialization. Analysis of world wars, the Cold War, and global change.</span></li>
                    <li><strong>History 11:</strong> <span id="notes-history-11">U.S. history from colonization to the 20th century. Focus on the Civil War, Reconstruction, and civil rights movements.</span></li>
                    <li><strong>History 12:</strong> <span id="notes-history-12">Government, politics, and contemporary issues. Covers globalization, current events, and research projects.</span></li>
                    <li><strong>Geography 9:</strong> <span id="notes-geography-9">Physical geography, maps, and landforms. Introduction to weather, climate, and the world’s continents and oceans.</span></li>
                    <li><strong>Geography 10:</strong> <span id="notes-geography-10">Human geography, population, and urbanization. Study of economic and cultural geography.</span></li>
                    <li><strong>Geography 11:</strong> <span id="notes-geography-11">Regional geography of the Americas, Europe, Asia, Africa, and Oceania. Comparative study of world regions.</span></li>
                    <li><strong>Geography 12:</strong> <span id="notes-geography-12">Environmental issues, geopolitics, and global interdependence. Advanced mapping and case studies.</span></li>
                    <li><strong>Civics 9:</strong> <span id="notes-civics-9">Foundations of government, the Constitution, and citizenship. Introduction to the branches of government and civic duties.</span></li>
                    <li><strong>Civics 10:</strong> <span id="notes-civics-10">Political parties, elections, and state/local government. Study of public policy and civic participation.</span></li>
                    <li><strong>Civics 11:</strong> <span id="notes-civics-11">Law, justice, and Supreme Court cases. Exploration of civil liberties and the role of media in society.</span></li>
                    <li><strong>Civics 12:</strong> <span id="notes-civics-12">Comparative governments, international relations, and civic engagement. Analysis of current events and global issues.</span></li>
                    <li><strong>World Cultures 9:</strong> <span id="notes-world-cultures-9">Cultural basics, religions, and traditions. Study of customs, diffusion, and cultural identity.</span></li>
                    <li><strong>World Cultures 10:</strong> <span id="notes-world-cultures-10">Major civilizations, art, and literature. Exploration of language, music, and dance across cultures.</span></li>
                    <li><strong>World Cultures 11:</strong> <span id="notes-world-cultures-11">Globalization, cultural conflicts, and migration. Examination of diaspora and modern cultural trends.</span></li>
                    <li><strong>World Cultures 12:</strong> <span id="notes-world-cultures-12">Case studies, cultural change, and technology. Focus on global citizenship and cultural identity in the modern world.</span></li>
                </ul>
            </div>
        </div>
    </section>
    <section id="grade-calculator-section">
        <h2>Grade Calculator</h2>
        <div id="grade-calculator" style="margin-bottom:20px;"></div>
    </section>
    <script>
        function updateClock() {
            const now = new Date();
            let h = now.getHours();
            let m = now.getMinutes();
            let s = now.getSeconds();
            const ampm = h >= 12 ? 'PM' : 'AM';
            h = h % 12;
            h = h ? h : 12;
            m = m < 10 ? '0' + m : m;
            s = s < 10 ? '0' + s : s;
            document.getElementById('clock').textContent = `${h}:${m}:${s} ${ampm}`;
        }
        setInterval(updateClock, 1000);
        updateClock();
        const gradeTopics = {
            math: {
                9: ["Algebra I", "Linear Equations", "Inequalities", "Functions", "Polynomials", "Basic Geometry"],
                10: ["Geometry", "Proofs", "Quadrilaterals", "Similarity & Congruence", "Right Triangles", "Trigonometry Basics"],
                11: ["Algebra II", "Quadratic Functions", "Exponential & Logarithmic Functions", "Sequences & Series", "Probability & Statistics"],
                12: ["Pre-Calculus", "Calculus (Intro)", "Limits & Derivatives", "Integrals", "Advanced Statistics", "Math Modeling"]
            },
            english: {
                9: ["Literature: Short Stories & Novels", "Grammar & Usage", "Essay Writing", "Poetry Analysis", "Vocabulary Building"],
                10: ["World Literature", "Research Papers", "Drama & Plays", "Persuasive Writing", "Public Speaking"],
                11: ["American Literature", "Critical Analysis", "SAT/ACT Prep", "Creative Writing", "Nonfiction Reading"],
                12: ["British Literature", "Advanced Composition", "Literary Criticism", "College Essays", "Speech & Debate"]
            },
            'physical-science': {
                9: ["Introduction to Physical Science", "Scientific Method", "Measurement & Units", "Basic Chemistry", "Basic Physics"],
                10: ["Chemistry: Atoms & Molecules", "Periodic Table", "Chemical Reactions", "Physics: Motion & Forces", "Energy & Work"],
                11: ["Physics: Waves & Sound", "Electricity & Magnetism", "Chemistry: Solutions & Acids/Bases", "Astronomy Basics"],
                12: ["Advanced Physics", "Nuclear Chemistry", "Earth & Space Science", "Environmental Science", "Research Projects"]
            },
            history: {
                9: ["World History Overview", "Ancient Civilizations", "Middle Ages", "Renaissance", "Exploration & Colonization"],
                10: ["Modern World History", "Revolutions (American, French, Haitian)", "Industrial Revolution", "World Wars I & II", "Cold War"],
                11: ["U.S. History: Colonization to Civil War", "Reconstruction", "Industrialization", "20th Century America", "Civil Rights Movement"],
                12: ["Government & Politics", "Contemporary World Issues", "Globalization", "Recent U.S. History", "Research Projects"]
            },
            geography: {
                9: ["Physical Geography Basics", "Maps & Globes", "Landforms", "Weather & Climate", "Continents & Oceans"],
                10: ["Human Geography", "Population & Migration", "Urbanization", "Cultural Geography", "Economic Geography"],
                11: ["Regional Geography", "North America", "South America", "Europe", "Asia", "Africa", "Australia & Oceania"],
                12: ["Environmental Issues", "Geopolitics", "Global Interdependence", "Advanced Mapping Skills", "Case Studies"]
            },
            civics: {
                9: ["Foundations of Government", "Constitution & Bill of Rights", "Branches of Government", "Citizenship"],
                10: ["Political Parties", "Elections & Voting", "State & Local Government", "Public Policy"],
                11: ["Law & Justice", "Supreme Court Cases", "Civil Liberties", "Role of Media"],
                12: ["Comparative Governments", "International Relations", "Civic Engagement", "Current Events"]
            },
            'world-cultures': {
                9: ["Cultural Basics", "World Religions", "Traditions & Customs", "Cultural Diffusion"],
                10: ["Major Civilizations", "Art & Architecture", "Language & Literature", "Music & Dance"],
                11: ["Globalization & Culture", "Cultural Conflicts", "Migration & Diaspora", "Modern Cultural Trends"],
                12: ["Case Studies by Region", "Cultural Identity", "Cultural Change & Technology", "Global Citizenship"]
            }
        };
        // --- Grade, Subject, and Class Descriptions ---
        const subjectDescriptions = {
  math: 'Mathematics develops problem-solving, logical reasoning, and quantitative skills. Explore algebra, geometry, statistics, and more.',
  english: 'English Language Arts focuses on reading, writing, grammar, and communication. Build skills in literature, essays, and analysis.',
  'physical-science': 'Physical Science covers chemistry, physics, and scientific inquiry. Learn about matter, energy, and the natural world.',
  history: 'History explores past events, cultures, and societies. Understand how the world has changed and why.',
  geography: 'Geography studies the Earth, its features, and human-environment interactions. Learn about maps, regions, and global issues.',
  civics: 'Civics teaches about government, citizenship, and civic responsibility. Discover how societies are organized and governed.',
  'world-cultures': 'World Cultures examines global traditions, beliefs, and cultural practices. Gain appreciation for diversity and global connections.'
};
const gradeDescriptions = {
  9: 'Grade 9: Foundation year for high school. Focus on core concepts and skills to prepare for advanced study.',
  10: 'Grade 10: Build on previous knowledge with more challenging material and critical thinking.',
  11: 'Grade 11: Advanced topics and preparation for college or careers. Emphasis on analysis and synthesis.',
  12: 'Grade 12: Capstone year. Mastery of subjects, independent projects, and readiness for graduation.'
};
const classDescriptions = {
  // Math
  'Algebra I': 'Introduction to algebraic concepts, variables, expressions, and solving simple equations.',
  'Linear Equations': 'Equations of the form ax + b = c. Learn to solve for x.',
  'Inequalities': 'Mathematical statements about the relative size of values. Solve and graph inequalities.',
  'Functions': 'A function relates each input to exactly one output. Explore linear, quadratic, and more.',
  'Polynomials': 'Expressions with multiple terms and exponents. Learn to add, subtract, multiply, and factor.',
  'Basic Geometry': 'Study of shapes, sizes, and properties of space. Includes area, perimeter, and volume.',
  'Geometry': 'Advanced study of geometric figures, proofs, and theorems.',
  'Proofs': 'Logical arguments demonstrating the truth of geometric statements.',
  'Quadrilaterals': 'Four-sided polygons. Calculate area, perimeter, and classify types.',
  'Similarity & Congruence': 'Compare shapes for similarity (same shape, different size) and congruence (same shape and size).',
  'Right Triangles': 'Triangles with a 90° angle. Use the Pythagorean theorem and trigonometric ratios.',
  'Trigonometry Basics': 'Study of relationships between angles and sides in triangles. Includes sine, cosine, and tangent.',
  'Algebra II': 'Advanced algebraic concepts: complex numbers, polynomials, and rational expressions.',
  'Quadratic Functions': 'Functions of the form ax² + bx + c. Graph and solve quadratics.',
  'Exponential & Logarithmic Functions': 'Functions involving exponents and logarithms. Growth, decay, and solving equations.',
  'Sequences & Series': 'Ordered lists of numbers and their sums. Arithmetic and geometric sequences.',
  'Probability & Statistics': 'Study of chance, data collection, analysis, and interpretation.',
  'Pre-Calculus': 'Preparation for calculus. Includes advanced algebra, trigonometry, and functions.',
  'Calculus (Intro)': 'Introduction to limits, derivatives, and integrals.',
  'Limits & Derivatives': 'Study of instantaneous rates of change and slopes of curves.',
  'Integrals': 'Study of accumulation of quantities and areas under curves.',
  'Advanced Statistics': 'In-depth data analysis, probability distributions, and inferential statistics.',
  'Math Modeling': 'Using mathematics to represent, analyze, and solve real-world problems.',
  // English
  'Literature: Short Stories & Novels': 'Read and analyze short stories and novels. Focus on plot, character, and theme.',
  'Grammar & Usage': 'Master the rules of English grammar and proper usage in writing and speech.',
  'Essay Writing': 'Develop skills in planning, drafting, and revising essays for various purposes.',
  'Poetry Analysis': 'Interpret and appreciate poetry. Study poetic devices, forms, and meaning.',
  'Vocabulary Building': 'Expand your vocabulary through roots, affixes, and context clues.',
  'World Literature': 'Explore literature from around the globe. Compare themes and styles.',
  'Research Papers': 'Learn to research, organize, and write academic papers with citations.',
  'Drama & Plays': 'Study dramatic literature and performance. Analyze structure and dialogue.',
  'Persuasive Writing': 'Write arguments and persuasive essays. Use evidence and rhetoric.',
  'Public Speaking': 'Practice effective oral communication and presentation skills.',
  'American Literature': 'Survey major works and authors in American literary history.',
  'Critical Analysis': 'Develop skills in literary criticism and textual analysis.',
  'SAT/ACT Prep': 'Prepare for standardized tests with reading, writing, and grammar practice.',
  'Creative Writing': 'Express yourself through fiction, poetry, and creative nonfiction.',
  'Nonfiction Reading': 'Read and analyze nonfiction texts for information and argument.',
  'British Literature': 'Study classic and modern works from British authors.',
  'Advanced Composition': 'Refine writing style, organization, and argumentation.',
  'Literary Criticism': 'Examine different approaches to interpreting literature.',
  'College Essays': 'Write effective personal statements and application essays.',
  'Speech & Debate': 'Develop skills in argumentation, debate, and public speaking.',
  // Physical Science
  'Introduction to Physical Science': 'Overview of scientific principles, methods, and measurement.',
  'Scientific Method': 'Steps for conducting scientific investigations: question, hypothesis, experiment, analysis, conclusion.',
  'Measurement & Units': 'Understanding and converting between units of measurement.',
  'Basic Chemistry': 'Study of matter, atoms, molecules, and chemical reactions.',
  'Basic Physics': 'Study of motion, forces, and energy.',
  'Chemistry: Atoms & Molecules': 'Structure of atoms, molecules, and the periodic table.',
  'Periodic Table': 'Organization of elements by properties and atomic number.',
  'Chemical Reactions': 'How substances interact to form new substances. Balancing equations.',
  'Physics: Motion & Forces': 'Study of movement, speed, velocity, acceleration, and Newton’s laws.',
  'Energy & Work': 'Concepts of energy, work, power, and conservation of energy.',
  'Physics: Waves & Sound': 'Study of wave properties, sound, and light.',
  'Electricity & Magnetism': 'Study of electric charges, circuits, and magnetic fields.',
  'Chemistry: Solutions & Acids/Bases': 'Properties of solutions, acids, and bases. pH scale.',
  'Astronomy Basics': 'Study of the universe, stars, planets, and galaxies.',
  'Advanced Physics': 'Topics in modern physics: relativity, quantum mechanics, and nuclear physics.',
  'Nuclear Chemistry': 'Study of radioactivity, nuclear reactions, and applications.',
  'Earth & Space Science': 'Study of Earth’s structure, atmosphere, and space exploration.',
  'Environmental Science': 'Study of ecosystems, resources, and human impact on the environment.',
  'Research Projects': 'Conducting scientific research and presenting findings.',
  // History
  'World History Overview': 'Survey of major world events, civilizations, and turning points.',
  'Ancient Civilizations': 'Study of early societies such as Egypt, Mesopotamia, and China.',
  'Middle Ages': 'Examine feudalism, the Crusades, and medieval society.',
  'Renaissance': 'Explore the rebirth of art, science, and culture in Europe.',
  'Exploration & Colonization': 'Learn about global exploration and the rise of empires.',
  'Modern World History': 'Analyze revolutions, industrialization, and world wars.',
  'Revolutions (American, French, Haitian)': 'Study causes and effects of major revolutions.',
  'Industrial Revolution': 'Examine technological and social changes in the 18th-19th centuries.',
  'World Wars I & II': 'Understand the causes, events, and consequences of the world wars.',
  'Cold War': 'Explore the global conflict between the US and USSR.',
  'U.S. History: Colonization to Civil War': 'Trace American history from early settlements to the Civil War.',
  'Reconstruction': 'Study the rebuilding of the US after the Civil War.',
  'Industrialization': 'Analyze the growth of industry and its impact on society.',
  '20th Century America': 'Explore key events and changes in modern US history.',
  'Civil Rights Movement': 'Learn about the struggle for equality and justice in America.',
  'Government & Politics': 'Understand political systems, ideologies, and institutions.',
  'Contemporary World Issues': 'Discuss current global challenges and trends.',
  'Globalization': 'Examine the interconnectedness of economies and cultures.',
  'Recent U.S. History': 'Study major events in the US from the late 20th century to today.',
  // Geography
  'Physical Geography Basics': 'Introduction to landforms, climate, and natural features.',
  'Maps & Globes': 'Learn to read and interpret maps and globes.',
  'Landforms': 'Study mountains, rivers, valleys, and other land features.',
  'Weather & Climate': 'Understand weather patterns and climate zones.',
  'Continents & Oceans': 'Identify continents, oceans, and their characteristics.',
  'Human Geography': 'Explore population, migration, and urbanization.',
  'Population & Migration': 'Study demographic trends and movement of people.',
  'Urbanization': 'Examine the growth and development of cities.',
  'Cultural Geography': 'Learn about cultural regions, language, and religion.',
  'Economic Geography': 'Study resources, trade, and economic systems.',
  'Regional Geography': 'Focus on specific world regions and their features.',
  'North America': 'Geography, culture, and history of North America.',
  'South America': 'Geography, culture, and history of South America.',
  'Europe': 'Geography, culture, and history of Europe.',
  'Asia': 'Geography, culture, and history of Asia.',
  'Africa': 'Geography, culture, and history of Africa.',
  'Australia & Oceania': 'Geography, culture, and history of Australia and Oceania.',
  'Environmental Issues': 'Study environmental challenges and sustainability.',
  'Geopolitics': 'Examine political geography and international relations.',
  'Global Interdependence': 'Understand how countries depend on each other.',
  'Advanced Mapping Skills': 'Develop advanced skills in map reading and analysis.',
  'Case Studies': 'In-depth studies of specific places or issues.',
  // Civics
  'Foundations of Government': 'Learn about the origins and purposes of government.',
  'Constitution & Bill of Rights': 'Study the US Constitution and the rights it guarantees.',
  'Branches of Government': 'Understand the legislative, executive, and judicial branches.',
  'Citizenship': 'Explore the rights and responsibilities of citizens.',
  'Political Parties': 'Learn about the role of parties in the political system.',
  'Elections & Voting': 'Study how elections work and why voting matters.',
  'State & Local Government': 'Examine government at the state and local levels.',
  'Public Policy': 'Understand how laws and policies are made.',
  'Law & Justice': 'Study the legal system and concepts of justice.',
  'Supreme Court Cases': 'Analyze landmark Supreme Court decisions.',
  'Civil Liberties': 'Learn about individual rights and freedoms.',
  'Role of Media': 'Examine the influence of media on society and politics.',
  'Comparative Governments': 'Compare different forms of government worldwide.',
  'International Relations': 'Study relationships between countries.',
  'Civic Engagement': 'Learn how to participate in civic life.',
  'Current Events': 'Discuss and analyze recent news and developments.',
  // World Cultures
  'Cultural Basics': 'Introduction to culture, traditions, and social norms.',
  'World Religions': 'Study major world religions and their beliefs.',
  'Traditions & Customs': 'Explore customs, rituals, and celebrations.',
  'Cultural Diffusion': 'Learn how cultures spread and influence each other.',
  'Major Civilizations': 'Study influential civilizations throughout history.',
  'Art & Architecture': 'Examine artistic and architectural achievements.',
  'Language & Literature': 'Explore languages and literary traditions.',
  'Music & Dance': 'Study music, dance, and their cultural significance.',
  'Globalization & Culture': 'Understand how globalization affects cultures.',
  'Cultural Conflicts': 'Examine conflicts arising from cultural differences.',
  'Migration & Diaspora': 'Study movement and settlement of peoples.',
  'Modern Cultural Trends': 'Explore current trends in global culture.',
  'Case Studies by Region': 'In-depth look at cultures in specific regions.',
  'Cultural Identity': 'Explore how identity is shaped by culture.',
  'Cultural Change & Technology': 'Study how technology changes cultures.',
  'Global Citizenship': 'Learn what it means to be a global citizen.'
};
// --- Render Descriptions in UI ---
function renderDescriptions(subject, grade) {
  let descHtml = '';
  if (subjectDescriptions[subject]) {
    descHtml += `<div style='margin-bottom:6px;'><strong>About this subject:</strong> ${subjectDescriptions[subject]}</div>`;
  }
  if (gradeDescriptions[grade]) {
    descHtml += `<div style='margin-bottom:6px;'><strong>About this grade:</strong> ${gradeDescriptions[grade]}</div>`;
  }
  return descHtml;
}
// Patch showGradeTopics to show subject/grade descriptions
const origShowGradeTopics = showGradeTopics;
showGradeTopics = function(select, subject) {
  const grade = select.value;
  const descDivId = subject + '-desc';
  let descDiv = document.getElementById(descDivId);
  if (!descDiv) {
    descDiv = document.createElement('div');
    descDiv.id = descDivId;
    select.parentNode.insertBefore(descDiv, select);
  }
  descDiv.innerHTML = grade ? renderDescriptions(subject, grade) : '';
  origShowGradeTopics(select, subject);
};
// Patch showTopicDetailsAndCalculator to show class descriptions
const origShowTopicDetailsAndCalculator = showTopicDetailsAndCalculator;
showTopicDetailsAndCalculator = function(subject, grade, topic) {
  const areaId = subject + '-calculator-area';
  let area = document.getElementById(areaId);
  if (!area) {
    origShowTopicDetailsAndCalculator(subject, grade, topic);
    area = document.getElementById(areaId);
  }
  if (topic && classDescriptions[topic]) {
    area.innerHTML = `<div style='margin-bottom:8px;'><strong>About this class:</strong> ${classDescriptions[topic]}</div>` + area.innerHTML;
  }
  origShowTopicDetailsAndCalculator(subject, grade, topic);
};
        function showGradeTopics(select, subject) {
            const grade = select.value;
            const topicSelect = document.getElementById(subject + '-topics');
            if (!grade) {
                topicSelect.style.display = 'none';
                topicSelect.innerHTML = '';
                if (subject === 'math' || subject === 'physical-science') {
                    document.getElementById(subject + '-calculator-area')?.remove();
                }
                return;
            }
            const topics = gradeTopics[subject][grade];
            topicSelect.innerHTML = '<option value="">Select Topic</option>' + topics.map(t => `<option>${t}</option>`).join('');
            topicSelect.style.display = '';
            // Add calculator area if not present
            if ((subject === 'math' || subject === 'physical-science') && !document.getElementById(subject + '-calculator-area')) {
                const area = document.createElement('div');
                area.id = subject + '-calculator-area';
                topicSelect.parentNode.appendChild(area);
            }
            topicSelect.onchange = function() { showTopicDetailsAndCalculator(subject, grade, topicSelect.value); };
        }

        // Topic descriptions for math and science
        const topicDescriptions = {
            // MATH
            'Algebra I': 'Introduction to algebraic concepts, variables, expressions, and solving simple equations.',
            'Linear Equations': 'Equations of the form ax + b = c. Learn to solve for x.',
            'Inequalities': 'Mathematical statements about the relative size of values. Solve and graph inequalities.',
            'Functions': 'A function relates each input to exactly one output. Explore linear, quadratic, and more.',
            'Polynomials': 'Expressions with multiple terms and exponents. Learn to add, subtract, multiply, and factor.',
            'Basic Geometry': 'Study of shapes, sizes, and properties of space. Includes area, perimeter, and volume.',
            'Geometry': 'Advanced study of geometric figures, proofs, and theorems.',
            'Proofs': 'Logical arguments demonstrating the truth of geometric statements.',
            'Quadrilaterals': 'Four-sided polygons. Calculate area, perimeter, and classify types.',
            'Similarity & Congruence': 'Compare shapes for similarity (same shape, different size) and congruence (same shape and size).',
            'Right Triangles': 'Triangles with a 90° angle. Use the Pythagorean theorem and trigonometric ratios.',
            'Trigonometry Basics': 'Study of relationships between angles and sides in triangles. Includes sine, cosine, and tangent.',
            'Algebra II': 'Advanced algebraic concepts: complex numbers, polynomials, and rational expressions.',
            'Quadratic Functions': 'Functions of the form ax² + bx + c. Graph and solve quadratics.',
            'Exponential & Logarithmic Functions': 'Functions involving exponents and logarithms. Growth, decay, and solving equations.',
            'Sequences & Series': 'Ordered lists of numbers and their sums. Arithmetic and geometric sequences.',
            'Probability & Statistics': 'Study of chance, data collection, analysis, and interpretation.',
            'Pre-Calculus': 'Preparation for calculus. Includes advanced algebra, trigonometry, and functions.',
            'Calculus (Intro)': 'Introduction to limits, derivatives, and integrals.',
            'Limits & Derivatives': 'Study of instantaneous rates of change and slopes of curves.',
            'Integrals': 'Study of accumulation of quantities and areas under curves.',
            'Advanced Statistics': 'In-depth data analysis, probability distributions, and inferential statistics.',
            'Math Modeling': 'Using mathematics to represent, analyze, and solve real-world problems.',
            // PHYSICAL SCIENCE
            'Introduction to Physical Science': 'Overview of scientific principles, methods, and measurement.',
            'Scientific Method': 'Steps for conducting scientific investigations: question, hypothesis, experiment, analysis, conclusion.',
            'Measurement & Units': 'Understanding and converting between units of measurement.',
            'Basic Chemistry': 'Study of matter, atoms, molecules, and chemical reactions.',
            'Basic Physics': 'Study of motion, forces, and energy.',
            'Chemistry: Atoms & Molecules': 'Structure of atoms, molecules, and the periodic table.',
            'Periodic Table': 'Organization of elements by properties and atomic number.',
            'Chemical Reactions': 'How substances interact to form new substances. Balancing equations.',
            'Physics: Motion & Forces': 'Study of movement, speed, velocity, acceleration, and Newton’s laws.',
            'Energy & Work': 'Concepts of energy, work, power, and conservation of energy.',
            'Physics: Waves & Sound': 'Study of wave properties, sound, and light.',
            'Electricity & Magnetism': 'Study of electric charges, circuits, and magnetic fields.',
            'Chemistry: Solutions & Acids/Bases': 'Properties of solutions, acids, and bases. pH scale.',
            'Astronomy Basics': 'Study of the universe, stars, planets, and galaxies.',
            'Advanced Physics': 'Topics in modern physics: relativity, quantum mechanics, and nuclear physics.',
            'Nuclear Chemistry': 'Study of radioactivity, nuclear reactions, and applications.',
            'Earth & Space Science': 'Study of Earth’s structure, atmosphere, and space exploration.',
            'Environmental Science': 'Study of ecosystems, resources, and human impact on the environment.',
            'Research Projects': 'Conducting scientific research and presenting findings.'
        };

        function showTopicDetailsAndCalculator(subject, grade, topic) {
            const areaId = subject + '-calculator-area';
            let area = document.getElementById(areaId);
            if (!area) {
                area = document.createElement('div');
                area.id = areaId;
                document.getElementById(subject + '-topics').parentNode.appendChild(area);
            }
            area.innerHTML = '';
            if (!topic) return;
            // Show topic description
            const desc = topicDescriptions[topic] || 'No description available.';
            area.innerHTML = `<div style='margin-bottom:10px;'><strong>About this topic:</strong> ${desc}</div>`;
            // Show gallery of note sheets for this subject/grade/topic
            const notesGallery = getNotesGallery(subject, grade, topic);
            if (notesGallery) {
                area.innerHTML += `<div style='margin-bottom:10px;'><strong>Note Sheet Gallery:</strong><div style='display:flex;gap:10px;flex-wrap:wrap;'>${notesGallery}</div></div>`;
            }
            // Show calculator/helper for each topic
            if (subject === 'math') {
                if (topic === 'Linear Equations') {
                    area.innerHTML += `<h4>Linear Equation Solver (ax + b = c)</h4>
                        <input type='number' id='le-a' placeholder='a' /> x +
                        <input type='number' id='le-b' placeholder='b' /> =
                        <input type='number' id='le-c' placeholder='c' />
                        <button onclick='solveLinearEquation()'>Solve</button>
                        <div id='le-result'></div>`;
                } else if (topic === 'Inequalities') {
                    area.innerHTML += `<h4>Inequality Solver (ax + b < c)</h4>
                        <input type='number' id='in-a' placeholder='a' /> x +
                        <input type='number' id='in-b' placeholder='b' /> <
                        <input type='number' id='in-c' placeholder='c' />
                        <button onclick='solveInequality()'>Solve</button>
                        <div id='in-result'></div>`;
                } else if (topic === 'Functions') {
                    area.innerHTML += `<h4>Function Calculator</h4>
                        <select id='func-type' onchange='showFunctionTypeCalc()'>
                            <option value=''>Select Type</option>
                            <option value='linear'>Linear</option>
                            <option value='quadratic'>Quadratic</option>
                            <option value='exponential'>Exponential</option>
                        </select>
                        <div id='functions-calc'></div>`;
                } else if (topic === 'Polynomials') {
                    area.innerHTML += `<h4>Polynomial Evaluator</h4>
                        <input type='text' id='poly-input' placeholder='e.g. 2x^2+3x-5' />
                        <button onclick='evaluatePolynomial()'>Evaluate at x = </button>
                        <input type='number' id='poly-x' placeholder='x' />
                        <div id='poly-result'></div>`;
                } else if (topic === 'Basic Geometry' || topic === 'Geometry') {
                    area.innerHTML += `<h4>Geometry Calculators</h4>
                        <button onclick='showAreaRectangleCalc()'>Area of Rectangle</button>
                        <button onclick='showAreaTriangleCalc()'>Area of Triangle</button>
                        <button onclick='showAreaCircleCalc()'>Area of Circle</button>
                        <div id='geometry-calc'></div>`;
                } else if (topic === 'Proofs') {
                    area.innerHTML += `<h4>Proofs Helper</h4><textarea rows='3' cols='40' placeholder='Statement'></textarea><br><textarea rows='3' cols='40' placeholder='Reason'></textarea>`;
                } else if (topic === 'Quadrilaterals') {
                    area.innerHTML += `<h4>Quadrilateral Area Calculator</h4>
                        <input type='number' id='quad-base' placeholder='Base' />
                        <input type='number' id='quad-height' placeholder='Height' />
                        <button onclick='calcQuadrilateralArea()'>Calculate</button>
                        <div id='quad-result'></div>`;
                } else if (topic === 'Similarity & Congruence') {
                    area.innerHTML += `<h4>Similarity & Congruence Checker</h4>
                        <input type='number' id='sim-a1' placeholder='a1' />
                        <input type='number' id='sim-b1' placeholder='b1' />
                        <input type='number' id='sim-c1' placeholder='c1' /><br>
                        <input type='number' id='sim-a2' placeholder='a2' />
                        <input type='number' id='sim-b2' placeholder='b2' />
                        <input type='number' id='sim-c2' placeholder='c2' />
                        <button onclick='checkSimilarity()'>Check</button>
                        <div id='sim-result'></div>`;
                } else if (topic === 'Right Triangles') {
                    area.innerHTML += `<h4>Pythagorean Theorem Calculator</h4>
                        <input type='number' id='pyth-a' placeholder='a' />
                        <input type='number' id='pyth-b' placeholder='b' />
                        <button onclick='calcPythagorean()'>Find c</button>
                        <div id='pyth-result'></div>`;
                } else if (topic === 'Trigonometry Basics') {
                    area.innerHTML += `<h4>Trigonometry Calculator</h4>
                        <input type='number' id='trig-angle' placeholder='Angle (degrees)' />
                        <button onclick='showTrigValues()'>Calculate sin, cos, tan</button>
                        <div id='trig-result'></div>`;
                } else if (topic === 'Algebra II') {
                    area.innerHTML += `<h4>Algebra II Calculators</h4>
                        <button onclick='showQuadraticFunctionCalc()'>Quadratic Function</button>
                        <button onclick='showExponentialFunctionCalc()'>Exponential Function</button>
                        <button onclick='showLogarithmicFunctionCalc()'>Logarithmic Function</button>
                        <div id='algebra2-calc'></div>`;
                } else if (topic === 'Quadratic Functions') {
                    showQuadraticFunctionCalc();
                } else if (topic === 'Exponential & Logarithmic Functions') {
                    area.innerHTML += `<h4>Exponential & Logarithmic Calculators</h4>
                        <button onclick='showExponentialFunctionCalc()'>Exponential Function</button>
                        <button onclick='showLogarithmicFunctionCalc()'>Logarithmic Function</button>
                        <div id='explog-calc'></div>`;
                } else if (topic === 'Sequences & Series') {
                    area.innerHTML += `<h4>Sequences & Series Calculator</h4>
                        <input type='number' id='seq-a1' placeholder='First term (a₁)' />
                        <input type='number' id='seq-d' placeholder='Common difference (d)' />
                        <input type='number' id='seq-n' placeholder='n' />
                        <button onclick='calcArithmeticSeq()'>Arithmetic nth Term</button>
                        <div id='seq-result'></div>`;
                } else if (topic === 'Probability & Statistics') {
                    area.innerHTML += `<h4>Probability Calculator</h4>
                        <input type='number' id='prob-fav' placeholder='Favorable' />
                        <input type='number' id='prob-total' placeholder='Total' />
                        <button onclick='calcProbability()'>Calculate</button>
                        <div id='prob-result'></div>
                        <h4>Statistics Calculator</h4>
                        <input type='text' id='stats-data' placeholder='Comma-separated data' />
                        <button onclick='calcStats()'>Calculate Mean/Median</button>
                        <div id='stats-result'></div>`;
                } else if (topic === 'Pre-Calculus') {
                    area.innerHTML += `<h4>Pre-Calculus Calculator</h4>
                        <input type='number' id='precalc-angle' placeholder='Angle (degrees)' />
                        <button onclick='showTrigValues()'>Trig Values</button>
                        <div id='trig-result'></div>`;
                } else if (topic === 'Calculus (Intro)' || topic === 'Limits & Derivatives' || topic === 'Integrals') {
                    area.innerHTML += `<h4>Calculus Helper</h4>
                        <input type='text' id='calc-func' placeholder='f(x)' />
                        <button onclick='calcDerivative()'>Derivative (approx)</button>
                        <button onclick='calcIntegral()'>Integral (approx)</button>
                        <input type='number' id='calc-a' placeholder='a' />
                        <input type='number' id='calc-b' placeholder='b' />
                        <div id='calc-result'></div>`;
                } else if (topic === 'Advanced Statistics') {
                    area.innerHTML += `<h4>Statistics Calculator</h4>
                        <input type='text' id='stats-data' placeholder='Comma-separated data' />
                        <button onclick='calcStats()'>Calculate Mean/Median</button>
                        <div id='stats-result'></div>`;
                } else if (topic === 'Math Modeling') {
                    area.innerHTML += `<h4>Math Modeling Helper</h4>
                        <textarea rows='3' cols='40' placeholder='Describe problem'></textarea>`;
                }
            } else if (subject === 'physical-science') {
                // Science calculators/helpers
                if (topic === 'Measurement & Units') {
                    area.innerHTML += `<h4>Unit Converter</h4>
                        <input type='number' id='unit-value' placeholder='Value' />
                        <select id='unit-from'>
                            <option value='cm'>cm</option><option value='m'>m</option><option value='km'>km</option><option value='in'>in</option><option value='ft'>ft</option><option value='yd'>yd</option><option value='mi'>mi</option>
                        </select>
                        to
                        <select id='unit-to'>
                            <option value='cm'>cm</option><option value='m'>m</option><option value='km'>km</option><option value='in'>in</option><option value='ft'>ft</option><option value='yd'>yd</option><option value='mi'>mi</option>
                        </select>
                        <button onclick='convertUnits()'>Convert</button>
                        <div id='unit-result'></div>`;
                } else if (topic === 'Basic Chemistry' || topic === 'Chemistry: Atoms & Molecules') {
                    area.innerHTML += `<h4>Molecular Mass Calculator</h4>
                        <input type='text' id='chem-formula' placeholder='H2O, CO2, etc.' />
                        <button onclick='calcMolecularMass()'>Calculate</button>
                        <div id='chem-result'></div>`;
                } else if (topic === 'Periodic Table') {
                    area.innerHTML += `<h4>Periodic Table Reference</h4>
                        <a href='https://ptable.com/' target='_blank'>Open Interactive Periodic Table</a>`;
                } else if (topic === 'Chemical Reactions') {
                    area.innerHTML += `<h4>Chemical Equation Balancer</h4>
                        <input type='text' id='chem-eq' placeholder='H2 + O2 = H2O' />
                        <button onclick='alert("Balancing not implemented. Use an online tool.")'>Balance</button>`;
                } else if (topic === 'Physics: Motion & Forces') {
                    area.innerHTML += `<h4>Motion Calculator</h4>
                        <input type='number' id='motion-d' placeholder='Distance (m)' />
                        <input type='number' id='motion-t' placeholder='Time (s)' />
                        <button onclick='calcSpeed()'>Speed = d/t</button>
                        <div id='motion-result'></div>`;
                } else if (topic === 'Energy & Work') {
                    area.innerHTML += `<h4>Work Calculator</h4>
                        <input type='number' id='work-f' placeholder='Force (N)' />
                        <input type='number' id='work-d' placeholder='Distance (m)' />
                        <button onclick='calcWork()'>Work = F × d</button>
                        <div id='work-result'></div>`;
                } else if (topic === 'Physics: Waves & Sound') {
                    area.innerHTML += `<h4>Wave Speed Calculator</h4>
                        <input type='number' id='wave-f' placeholder='Frequency (Hz)' />
                        <input type='number' id='wave-l' placeholder='Wavelength (m)' />
                        <button onclick='calcWaveSpeed()'>v = f × λ</button>
                        <div id='wave-result'></div>`;
                } else if (topic === 'Electricity & Magnetism') {
                    area.innerHTML += `<h4>Ohm's Law Calculator</h4>
                        <input type='number' id='ohm-v' placeholder='Voltage (V)' />
                        <input type='number' id='ohm-r' placeholder='Resistance (Ω)' />
                        <button onclick='calcOhmsLaw()'>I = V / R</button>
                        <div id='ohm-result'></div>`;
                } else if (topic === 'Chemistry: Solutions & Acids/Bases') {
                    area.innerHTML += `<h4>pH Calculator</h4>
                        <input type='number' id='ph-h' placeholder='[H+], mol/L' />
                        <button onclick='calcPH()'>Calculate pH</button>
                        <div id='ph-result'></div>`;
                } else if (topic === 'Astronomy Basics') {
                    area.innerHTML += `<h4>Solar System Reference</h4>
                        <a href='https://solarsystem.nasa.gov/planets/overview/' target='_blank'>NASA Solar System Overview</a>`;
                } else if (topic === 'Advanced Physics') {
                    area.innerHTML += `<h4>Relativity Calculator</h4>
                        <input type='number' id='rel-v' placeholder='Speed (m/s)' />
                        <button onclick='calcRelativity()'>γ = 1 / sqrt(1 - v²/c²)</button>
                        <div id='rel-result'></div>`;
                } else if (topic === 'Nuclear Chemistry') {
                    area.innerHTML += `<h4>Half-Life Calculator</h4>
                        <input type='number' id='hl-n0' placeholder='Initial Amount' />
                        <input type='number' id='hl-t' placeholder='Elapsed Time' />
                        <input type='number' id='hl-hl' placeholder='Half-life' />
                        <button onclick='calcHalfLife()'>Calculate Remaining</button>
                        <div id='hl-result'></div>`;
                } else if (topic === 'Earth & Space Science') {
                    area.innerHTML += `<h4>Earth Layers Reference</h4>
                        <a href='https://www.usgs.gov/special-topics/earth-science-school/science/structure-earth' target='_blank'>USGS Earth Structure</a>`;
                } else if (topic === 'Environmental Science') {
                    area.innerHTML += `<h4>Carbon Footprint Estimator</h4>
                        <input type='number' id='cf-miles' placeholder='Miles Driven/Week' />
                        <button onclick='calcCarbonFootprint()'>Estimate CO₂</button>
                        <div id='cf-result'></div>`;
                } else if (topic === 'Research Projects') {
                    area.innerHTML += `<h4>Research Project Helper</h4>
                        <textarea rows='3' cols='40' placeholder='Describe your project'></textarea>`;
                } else if (topic === 'Scientific Method' || topic === 'Introduction to Physical Science') {
                    area.innerHTML += `<h4>Scientific Method Steps</h4><ol><li>Ask a Question</li><li>Do Background Research</li><li>Construct a Hypothesis</li><li>Test with Experiments</li><li>Analyze Data</li><li>Draw Conclusions</li></ol>`;
                }
            }
        }
        // --- Function type calculator for math ---
        function showFunctionTypeCalc() {
            var type = document.getElementById('func-type').value;
            var area = document.getElementById('functions-calc');
            if (!type) { area.innerHTML = ''; return; }
            if (type === 'linear') {
                area.innerHTML = `<h4>Linear Function f(x) = mx + b</h4>
                    <input type='number' id='lf-m' placeholder='m' /> x +
                    <input type='number' id='lf-b' placeholder='b' />, x =
                    <input type='number' id='lf-x' placeholder='x' />
                    <button onclick='calcLinearFunction()'>Calculate</button>
                    <div id='lf-result'></div>`;
            } else if (type === 'quadratic') {
                area.innerHTML = `<h4>Quadratic Function f(x) = ax² + bx + c</h4>
                    <input type='number' id='qf-a' placeholder='a' /> x² +
                    <input type='number' id='qf-b' placeholder='b' /> x +
                    <input type='number' id='qf-c' placeholder='c' />, x =
                    <input type='number' id='qf-x' placeholder='x' />
                    <button onclick='calcQuadraticFunction()'>Calculate</button>
                    <div id='qf-result'></div>`;
            } else if (type === 'exponential') {
                area.innerHTML = `<h4>Exponential Function f(x) = a·b^x</h4>
                    <input type='number' id='ef-a' placeholder='a' /> ·
                    <input type='number' id='ef-b' placeholder='b' /> ^
                    <input type='number' id='ef-x' placeholder='x' />
                    <button onclick='calcExponentialFunction()'>Calculate</button>
                    <div id='ef-result'></div>`;
            }
        }
        function calcQuadrilateralArea() {
            const base = parseFloat(document.getElementById('quad-base').value);
            const height = parseFloat(document.getElementById('quad-height').value);
            let result = '';
            if (!isNaN(base) && !isNaN(height)) {
                result = `Area: ${base * height}`;
            } else {
                result = 'Please enter valid numbers for base and height.';
            }
            document.getElementById('quad-result').innerText = result;
        }

        // --- Grade Calculator ---
        (function renderGradeCalculator() {
            const container = document.getElementById('grade-calculator');
            if (!container) return;
            container.innerHTML = `
                <div style='max-width:500px;'>
                    <label>Current Overall Grade (%): <input type='number' id='gc-overall' min='0' max='100' step='0.01' /></label><br><br>
                    <label>Assignment Weight (% of total): <input type='number' id='gc-weight' min='0' max='100' step='0.01' /></label><br><br>
                    <label>Assignment Grade (%): <input type='number' id='gc-assignment' min='0' max='100' step='0.01' value='0' /></label><br><br>
                    <button onclick='calcNewGrade()'>Calculate New Overall</button>
                    <div id='gc-result' style='margin-top:10px;'></div>
                </div>
            `;
        })();

        function calcNewGrade() {
            const overall = parseFloat(document.getElementById('gc-overall').value);
            const weight = parseFloat(document.getElementById('gc-weight').value);
            const assignment = parseFloat(document.getElementById('gc-assignment').value);
            let result = '';
            if (
                isNaN(overall) || overall < 0 || overall > 100 ||
                isNaN(weight) || weight <= 0 || weight > 100 ||
                isNaN(assignment) || assignment < 0 || assignment > 100
            ) {
                result = 'Please enter valid numbers for all fields.';
            } else {
                // Calculate new overall: weighted average
                const remainingWeight = 100 - weight;
                const newOverall = ((overall * remainingWeight) + (assignment * weight)) / 100;
                result = `Your new overall grade would be <strong>${newOverall.toFixed(2)}%</strong> if you score ${assignment}% on this assignment.`;
            }
            document.getElementById('gc-result').innerHTML = result;
        }

        // Helper to get note sheet gallery HTML for a subject/grade/topic
        function getNotesGallery(subject, grade, topic) {
            // Example: You can expand this with more detailed note sheets per topic/grade/subject
            const notesData = {
                math: {
                    9: {
                        'Algebra I': [
                            { name: 'Variables & Expressions', img: 'notes/math/9/algebra-variables.jpg' },
                            { name: 'Solving Equations', img: 'notes/math/9/algebra-equations.jpg' },
                            { name: 'Graphing Lines', img: 'notes/math/9/algebra-graphing.jpg' }
                        ],
                        'Linear Equations': [
                            { name: 'Slope-Intercept Form', img: 'notes/math/9/linear-slope.jpg' },
                            { name: 'Standard Form', img: 'notes/math/9/linear-standard.jpg' },
                            { name: 'Graphing', img: 'notes/math/9/linear-graphing.jpg' }
                        ],
                        'Inequalities': [
                            { name: 'Solving Inequalities', img: 'notes/math/9/inequalities-solving.jpg' },
                            { name: 'Graphing Solutions', img: 'notes/math/9/inequalities-graphing.jpg' }
                        ],
                        'Functions': [
                            { name: 'Domain & Range', img: 'notes/math/9/functions-domain.jpg' },
                            { name: 'Function Notation', img: 'notes/math/9/functions-notation.jpg' }
                        ],
                        'Polynomials': [
                            { name: 'Adding/Subtracting', img: 'notes/math/9/polynomials-addsub.jpg' },
                            { name: 'Multiplying', img: 'notes/math/9/polynomials-mult.jpg' },
                            { name: 'Factoring', img: 'notes/math/9/polynomials-factoring.jpg' }
                        ],
                        'Basic Geometry': [
                            { name: 'Area & Perimeter', img: 'notes/math/9/geometry-area.jpg' },
                            { name: 'Types of Angles', img: 'notes/math/9/geometry-angles.jpg' },
                            { name: 'Triangles', img: 'notes/math/9/geometry-triangles.jpg' }
                        ]
                    },
                    10: {
                        'Geometry': [
                            { name: 'Proof Strategies', img: 'notes/math/10/geometry-proofs.jpg' },
                            { name: 'Triangle Properties', img: 'notes/math/10/geometry-triangles.jpg' },
                            { name: 'Circle Theorems', img: 'notes/math/10/geometry-circles.jpg' }
                        ],
                        'Proofs': [
                            { name: 'Two-Column Proofs', img: 'notes/math/10/proofs-twocolumn.jpg' },
                            { name: 'Common Theorems', img: 'notes/math/10/proofs-theorems.jpg' }
                        ],
                        'Quadrilaterals': [
                            { name: 'Types of Quads', img: 'notes/math/10/quads-types.jpg' },
                            { name: 'Area Formulas', img: 'notes/math/10/quads-area.jpg' }
                        ],
                        'Similarity & Congruence': [
                            { name: 'AA, SAS, SSS', img: 'notes/math/10/similarity-aa-sas-sss.jpg' },
                            { name: 'CPCTC', img: 'notes/math/10/similarity-cpctc.jpg' }
                        ],
                        'Right Triangles': [
                            { name: 'Pythagorean Theorem', img: 'notes/math/10/righttriangles-pythagorean.jpg' },
                            { name: 'Special Right Triangles', img: 'notes/math/10/righttriangles-special.jpg' }
                        ],
                        'Trigonometry Basics': [
                            { name: 'SOHCAHTOA', img: 'notes/math/10/trig-sohcahtoa.jpg' },
                            { name: 'Unit Circle', img: 'notes/math/10/trig-unitcircle.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                },
                english: {
                    9: {
                        'Literature: Short Stories & Novels': [
                            { name: 'Plot Elements', img: 'notes/english/9/lit-plot.jpg' },
                            { name: 'Characterization', img: 'notes/english/9/lit-characters.jpg' },
                            { name: 'Theme', img: 'notes/english/9/lit-theme.jpg' }
                        ],
                        'Grammar & Usage': [
                            { name: 'Parts of Speech', img: 'notes/english/9/grammar-parts.jpg' },
                            { name: 'Sentence Structure', img: 'notes/english/9/grammar-sentences.jpg' }
                        ],
                        'Essay Writing': [
                            { name: 'Thesis Statements', img: 'notes/english/9/essay-thesis.jpg' },
                            { name: 'Paragraph Structure', img: 'notes/english/9/essay-paragraph.jpg' }
                        ],
                        'Poetry Analysis': [
                            { name: 'Poetic Devices', img: 'notes/english/9/poetry-devices.jpg' },
                            { name: 'Rhyme & Meter', img: 'notes/english/9/poetry-rhyme.jpg' }
                        ],
                        'Vocabulary Building': [
                            { name: 'Roots & Affixes', img: 'notes/english/9/vocab-roots.jpg' },
                            { name: 'Context Clues', img: 'notes/english/9/vocab-context.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                },
                'physical-science': {
                    9: {
                        'Introduction to Physical Science': [
                            { name: 'Scientific Method', img: 'notes/science/9/intro-scimethod.jpg' },
                            { name: 'Lab Safety', img: 'notes/science/9/intro-labsafety.jpg' }
                        ],
                        'Scientific Method': [
                            { name: 'Steps', img: 'notes/science/9/scimethod-steps.jpg' },
                            { name: 'Variables', img: 'notes/science/9/scimethod-variables.jpg' }
                        ],
                        'Measurement & Units': [
                            { name: 'SI Units', img: 'notes/science/9/units-si.jpg' },
                            { name: 'Conversions', img: 'notes/science/9/units-conversions.jpg' }
                        ],
                        'Basic Chemistry': [
                            { name: 'Atoms', img: 'notes/science/9/chem-atoms.jpg' },
                            { name: 'Molecules', img: 'notes/science/9/chem-molecules.jpg' }
                        ],
                        'Basic Physics': [
                            { name: 'Motion', img: 'notes/science/9/physics-motion.jpg' },
                            { name: 'Forces', img: 'notes/science/9/physics-forces.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                },
                history: {
                    9: {
                        'World History Overview': [
                            { name: 'Timeline', img: 'notes/history/9/world-timeline.jpg' },
                            { name: 'Major Civilizations', img: 'notes/history/9/world-civilizations.jpg' }
                        ],
                        'Ancient Civilizations': [
                            { name: 'Egypt', img: 'notes/history/9/ancient-egypt.jpg' },
                            { name: 'Mesopotamia', img: 'notes/history/9/ancient-mesopotamia.jpg' },
                            { name: 'China', img: 'notes/history/9/ancient-china.jpg' }
                        ],
                        'Middle Ages': [
                            { name: 'Feudalism', img: 'notes/history/9/middleages-feudalism.jpg' },
                            { name: 'Crusades', img: 'notes/history/9/middleages-crusades.jpg' }
                        ],
                        'Renaissance': [
                            { name: 'Art & Science', img: 'notes/history/9/renaissance-art.jpg' },
                            { name: 'Humanism', img: 'notes/history/9/renaissance-humanism.jpg' }
                        ],
                        'Exploration & Colonization': [
                            { name: 'Age of Exploration', img: 'notes/history/9/explore-age.jpg' },
                            { name: 'Colonial Empires', img: 'notes/history/9/explore-colonial.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                },
                geography: {
                    9: {
                        'Physical Geography Basics': [
                            { name: 'Landforms', img: 'notes/geography/9/phys-landforms.jpg' },
                            { name: 'Climate Zones', img: 'notes/geography/9/phys-climate.jpg' }
                        ],
                        'Maps & Globes': [
                            { name: 'Latitude/Longitude', img: 'notes/geography/9/maps-latlong.jpg' },
                            { name: 'Map Projections', img: 'notes/geography/9/maps-projections.jpg' }
                        ],
                        'Landforms': [
                            { name: 'Mountains', img: 'notes/geography/9/landforms-mountains.jpg' },
                            { name: 'Rivers', img: 'notes/geography/9/landforms-rivers.jpg' }
                        ],
                        'Weather & Climate': [
                            { name: 'Weather vs. Climate', img: 'notes/geography/9/weather-vs-climate.jpg' },
                            { name: 'Global Patterns', img: 'notes/geography/9/weather-global.jpg' }
                        ],
                        'Continents & Oceans': [
                            { name: 'World Map', img: 'notes/geography/9/continents-map.jpg' },
                            { name: 'Major Oceans', img: 'notes/geography/9/continents-oceans.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                },
                civics: {
                    9: {
                        'Foundations of Government': [
                            { name: 'Types of Government', img: 'notes/civics/9/gov-types.jpg' },
                            { name: 'Constitution', img: 'notes/civics/9/gov-constitution.jpg' }
                        ],
                        'Constitution & Bill of Rights': [
                            { name: 'Amendments', img: 'notes/civics/9/constitution-amendments.jpg' },
                            { name: 'Principles', img: 'notes/civics/9/constitution-principles.jpg' }
                        ],
                        'Branches of Government': [
                            { name: 'Legislative', img: 'notes/civics/9/branches-legislative.jpg' },
                            { name: 'Executive', img: 'notes/civics/9/branches-executive.jpg' },
                            { name: 'Judicial', img: 'notes/civics/9/branches-judicial.jpg' }
                        ],
                        'Citizenship': [
                            { name: 'Rights & Responsibilities', img: 'notes/civics/9/citizenship-rights.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                },
                'world-cultures': {
                    9: {
                        'Cultural Basics': [
                            { name: 'Culture Traits', img: 'notes/world-cultures/9/culture-traits.jpg' },
                            { name: 'Cultural Diffusion', img: 'notes/world-cultures/9/culture-diffusion.jpg' }
                        ],
                        'World Religions': [
                            { name: 'Major Religions', img: 'notes/world-cultures/9/religions-major.jpg' },
                            { name: 'Beliefs', img: 'notes/world-cultures/9/religions-beliefs.jpg' }
                        ],
                        'Traditions & Customs': [
                            { name: 'Holidays', img: 'notes/world-cultures/9/traditions-holidays.jpg' },
                            { name: 'Rituals', img: 'notes/world-cultures/9/traditions-rituals.jpg' }
                        ],
                        'Cultural Diffusion': [
                            { name: 'Examples', img: 'notes/world-cultures/9/diffusion-examples.jpg' },
                            { name: 'Effects', img: 'notes/world-cultures/9/diffusion-effects.jpg' }
                        ]
                    },
                    // ...add more for other grades/topics...
                }
            };
            if (notesData[subject] && notesData[subject][grade] && notesData[subject][grade][topic]) {
                return notesData[subject][grade][topic].map(
                    (sheet, idx) => `<div style='background:#f8f9fb;border:1px solid #e0e4ea;border-radius:6px;padding:8px 12px;min-width:120px;text-align:center;'><a href='${sheet.img}' target='_blank' style='color:#2d3e50;text-decoration:underline;'>${sheet.name}</a></div>`
                ).join('');
            }
            return '';
        }
        // --- Physical Science Calculators Output Logic ---
        function convertUnits() {
            const value = parseFloat(document.getElementById('unit-value').value);
            const from = document.getElementById('unit-from').value;
            const to = document.getElementById('unit-to').value;
                       let result = '';
            if (isNaN(value)) {
                result = 'Please enter a valid number.';
            } else {
                // Conversion factors to meters
                const toMeters = {
                    cm: 0.01, m: 1, km: 1000, in: 0.0254, ft: 0.3048, yd: 0.9144, mi: 1609.34
                };
                if (!(from in toMeters) || !(to in toMeters)) {
                    result = 'Invalid units.';
                } else {
                    const meters = value * toMeters[from];
                    const converted = meters / toMeters[to];
                    result = `${value} ${from} = ${converted.toFixed(4)} ${to}`;
                }
            }
            document.getElementById('unit-result').innerText = result;
        }

        function calcMolecularMass() {
            const formula = document.getElementById('chem-formula').value.trim();
            let result = '';
            if (!formula) {
                result = 'Please enter a chemical formula.';
            } else {
                // Simple atomic mass table (expand as needed)
                const massTable = {H:1.008, He:4.003, C:12.01, N:14.01, O:16.00, Na:22.99, Cl:35.45, S:32.07, P:30.97, K:39.10, Ca:40.08, Fe:55.85, Mg:24.31, Al:26.98, Si:28.09, F:18.998, Zn:65.38, Cu:63.55};
                // Regex to parse formula (e.g., H2O, CO2)
                let mass = 0;
                let match;
                const regex = /([A-Z][a-z]?)(\d*)/g;
                while ((match = regex.exec(formula)) !== null) {
                    const elem = match[1];
                    const count = parseInt(match[2] || '1', 10);
                    if (!(elem in massTable)) {
                        result = `Unknown element: ${elem}`;
                        document.getElementById('chem-result').innerText = result;
                        return;
                    }
                    mass += massTable[elem] * count;
                }
                result = `Molecular mass of ${formula}: ${mass.toFixed(3)} g/mol`;
            }
            document.getElementById('chem-result').innerText = result;
        }

        function calcSpeed() {
            const d = parseFloat(document.getElementById('motion-d').value);
            const t = parseFloat(document.getElementById('motion-t').value);
            let result = '';
            if (isNaN(d) || isNaN(t) || t === 0) {
                result = 'Please enter valid numbers (time ≠ 0).';
            } else {
                result = `Speed: ${(d / t).toFixed(3)} m/s`;
            }
            document.getElementById('motion-result').innerText = result;
        }

        function calcWork() {
            const f = parseFloat(document.getElementById('work-f').value);
            const d = parseFloat(document.getElementById('work-d').value);
            let result = '';
            if (isNaN(f) || isNaN(d)) {
                result = 'Please enter valid numbers for force and distance.';
            } else {
                result = `Work: ${(f * d).toFixed(3)} J`;
            }
            document.getElementById('work-result').innerText = result;
        }

        function calcWaveSpeed() {
            const freq = parseFloat(document.getElementById('wave-f').value);
            const lambda = parseFloat(document.getElementById('wave-l').value);
            let result = '';
            if (isNaN(freq) || isNaN(lambda)) {
                result = 'Please enter valid numbers for frequency and wavelength.';
            } else {
                result = `Wave speed: ${(freq * lambda).toFixed(3)} m/s`;
            }
            document.getElementById('wave-result').innerText = result;
        }

        function calcOhmsLaw() {
            const v = parseFloat(document.getElementById('ohm-v').value);
            const r = parseFloat(document.getElementById('ohm-r').value);
            let result = '';
            if (isNaN(v) || isNaN(r) || r === 0) {
                result = 'Please enter valid numbers (resistance ≠ 0).';
            } else {
                result = `Current: ${(v / r).toFixed(3)} A`;
            }
            document.getElementById('ohm-result').innerText = result;
        }

        function calcPH() {
            const h = parseFloat(document.getElementById('ph-h').value);
            let result = '';
            if (isNaN(h) || h <= 0) {
                result = 'Please enter a valid [H+] (> 0).';
            } else {
                result = `pH: ${(-Math.log10(h)).toFixed(2)}`;
            }
            document.getElementById('ph-result').innerText = result;
        }

        function calcRelativity() {
            const v = parseFloat(document.getElementById('rel-v').value);
            const c = 299792458; // speed of light in m/s
            let result = '';
            if (isNaN(v) || v < 0 || v >= c) {
                result = 'Please enter a valid speed (0 ≤ v < c).';
            } else {
                const gamma = 1 / Math.sqrt(1 - (v * v) / (c * c));
                result = `γ (Lorentz factor): ${gamma.toFixed(5)}`;
            }
            document.getElementById('rel-result').innerText = result;
        }

        function calcHalfLife() {
            const n0 = parseFloat(document.getElementById('hl-n0').value);
            const t = parseFloat(document.getElementById('hl-t').value);
            const hl = parseFloat(document.getElementById('hl-hl').value);
            let result = '';
            if (isNaN(n0) || isNaN(t) || isNaN(hl) || hl <= 0) {
                result = 'Please enter valid numbers (half-life > 0).';
            } else {
                const n = n0 * Math.pow(0.5, t / hl);
                result = `Remaining amount: ${n.toFixed(4)}`;
            }
            document.getElementById('hl-result').innerText = result;
        }

        function calcCarbonFootprint() {
            const miles = parseFloat(document.getElementById('cf-miles').value);
            let result = '';
            if (isNaN(miles) || miles < 0) {
                result = 'Please enter a valid number of miles.';
            } else {
                // Average car emits ~404g CO2 per mile
                const co2 = miles * 404;
                result = `Estimated CO₂: ${(co2 / 1000).toFixed(2)} kg/week`;
            }
            document.getElementById('cf-result').innerText = result;
        }

        // Add Essay Corrector to English section after the English notes list
        const englishSection = document.getElementById('english');
        if (englishSection && !document.getElementById('essay-corrector-section')) {
            const essayDiv = document.createElement('div');
            essayDiv.id = 'essay-corrector-section';
            essayDiv.innerHTML = `
                <h3>Essay Corrector</h3>
                <label for='ec-grade'>Select Grade Level: </label>
                <select id='ec-grade'>
                    <option value='9'>9th Grade</option>
                    <option value='10'>10th Grade</option>
                    <option value='11'>11th Grade</option>
                    <option value='12'>12th Grade</option>
                </select><br><br>
                <textarea id='ec-essay' rows='8' cols='70' placeholder='Paste your essay here...'></textarea><br>
                <button onclick='runEssayCorrector()'>Check Essay</button>
                <div id='ec-result' style='margin-top:12px;'></div>
            `;
            englishSection.appendChild(essayDiv);
        }

        function runEssayCorrector() {
            const grade = document.getElementById('ec-grade').value;
            const essay = document.getElementById('ec-essay').value;
            let result = '';
            if (!essay.trim()) {
                document.getElementById('ec-result').innerHTML = 'Please paste your essay.';
                return;
            }
            // Basic spelling/grammar checks
            const commonMistakes = [
                { regex: /\bi\b/g, suggestion: 'I (capitalize first person singular)' },
                { regex: /\bteh\b/g, suggestion: 'the' },
                { regex: /\brecieve\b/g, suggestion: 'receive' },
                { regex: /\bdefinately\b/g, suggestion: 'definitely' },
                { regex: /\bseperate\b/g, suggestion: 'separate' },
                { regex: /\bwich\b/g, suggestion: 'which' },
                { regex: /\btheir\s+is\b/g, suggestion: 'there is' },
                { regex: /\byour\s+welcome\b/g, suggestion: 'you\'re welcome' },
                { regex: /\b alot\b/g, suggestion: 'a lot' }
            ];
            let issues = [];
            commonMistakes.forEach(m => {
                if (m.regex.test(essay)) {
                    issues.push(`Possible mistake: <mark>${m.regex.source.replace(/\\b/g, '')}</mark> → Suggestion: <strong>${m.suggestion}</strong>`);
                }
            });
            // Grade-level requirements
            let gradeReqs = '';
            if (grade == '9') {
                gradeReqs = 'Check for complete sentences, basic punctuation, and common spelling errors.';
            } else if (grade == '10') {
                gradeReqs = 'Check for varied sentence structure, correct use of commas/semicolons, and subject-verb agreement.';
                // Add a check for repeated words
                const repeated = essay.match(/\b(\w+) \1\b/gi);
                if (repeated) {
                    issues.push(`Repeated word(s): <mark>${repeated.join(', ')}</mark>`);
                }
            } else if (grade == '11') {
                gradeReqs = 'Check for advanced punctuation, parallel structure, and transition words.';
                // Check for missing transition words
                const transitions = ['however', 'therefore', 'moreover', 'consequently', 'furthermore'];
                const found = transitions.some(t => essay.toLowerCase().includes(t));
                if (!found) {
                    issues.push('Consider adding transition words (e.g., however, therefore, moreover).');
                }
            } else if (grade == '12') {
                gradeReqs = 'Check for sophisticated vocabulary, advanced grammar, and logical flow.';
                // Check for passive voice (simple heuristic)
                const passive = essay.match(/\b(is|was|were|be|been|being|are|am) [a-z]+ed\b/gi);
                if (passive) {
                    issues.push(`Possible passive voice: <mark>${passive.join(', ')}</mark>`);
                }
            }
            result += `<div><strong>Grade ${grade} Requirements:</strong> ${gradeReqs}</div>`;
            if (issues.length > 0) {
                result += `<ul style='color:#b00;'>` + issues.map(i => `<li>${i}</li>`).join('') + `</ul>`;
            } else {
                result += `<div style='color:green;'>No major issues detected. Good job!</div>`;
            }
            document.getElementById('ec-result').innerHTML = result;
        }

        // Show chat box on hover or focus
const aiHead = document.getElementById('ai-character-head');
const aiChatBox = document.getElementById('ai-chat-box');
let aiChatOpen = false; //HISHISHIS
function openAiChat() {
  aiHead.classList.add('ai-chat-open');
  aiChatBox.classList.add('ai-chat-open');
  aiChatBox.style.display = 'block';
  aiChatOpen = true;
}
function closeAiChat() {
  aiHead.classList.remove('ai-chat-open');
  aiChatBox.classList.remove('ai-chat-open');
  setTimeout(() => { if (!aiChatOpen) aiChatBox.style.display = 'none'; }, 350);
  aiChatOpen = false;
}
aiHead.addEventListener('mouseenter', openAiChat);
aiHead.addEventListener('mouseleave', () => setTimeout(() => { if (!aiChatBox.matches(':hover')) closeAiChat(); }, 300));
aiChatBox.addEventListener('mouseleave', closeAiChat);
aiChatBox.addEventListener('mouseenter', openAiChat);
document.getElementById('ai-chat-input').addEventListener('keydown', function(e) {
  if (e.key === 'Enter') document.getElementById('ai-chat-send').click();
});
document.getElementById('ai-chat-send').onclick = async function() {
  const input = document.getElementById('ai-chat-input');
  const responseDiv = document.getElementById('ai-chat-response');
  const question = input.value.trim();
  if (!question) return;
  responseDiv.innerHTML = '<em>Thinking...</em>';
  input.value = '';
  // --- Real AI answer integration (OpenAI API or similar) ---
  try {
    // Replace this with your real API call if you have an endpoint
    // Example: const answer = await fetchAiAnswer(question);
    const answer = await fetchAiAnswer(question);
    responseDiv.innerHTML = answer;
  } catch (e) {
    responseDiv.innerHTML = 'Sorry, I could not get an answer right now.';
  }
};
// Simulated AI answer function (replace with real API call)
async function fetchAiAnswer(question) {
  // You can replace this with a real fetch to OpenAI or another LLM endpoint
  // Example:
  // const resp = await fetch('https://api.openai.com/v1/chat/completions', { ... });
  // const data = await resp.json();
  // return data.choices[0].message.content;
  // For now, use a placeholder:
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('Here is an AI-generated answer to your question: <br><strong>' + question.replace(/</g,'&lt;').replace(/>/g,'&gt;') + '</strong>');
    }, 1200);
  });
}
    </script>
    <!-- Place cartoon character just before </body> -->
    <div id="ai-character-container">
  <div id="ai-character-head">
    <div id="ai-character-head-inner">
      <div class="ai-eye"></div>
      <div class="ai-mouth"></div>
    </div>
  </div>
  <div id="ai-chat-box">
    <div id="ai-chat-response" style="min-height:36px;"></div>
    <div id="ai-chat-input-row">
      <input id="ai-chat-input" type="text" placeholder="Ask me anything..." />
      <button id="ai-chat-send">Ask</button>
    </div>
  </div>
</div>
</body>
<!--Need to add information to the drop down menu.-->
<!--Also add when I go to the specific grade and subject in the math tab can you add calculators to solve problems in that subject for wherever it is possible please -->
<!--Can you add an interactible only visible to the person typing text box that sends a message to my personal email about a suggestion-->
