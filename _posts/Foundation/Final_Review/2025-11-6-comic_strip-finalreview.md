---
layout: post
title:  Walking Through A comic
description: Collaboration + commits descirption
categories: ['Collaboration']
permalink: /comic_strip
date: 2025-10-21
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Official Commits & Collaboration</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0d1117;
            font-family: 'Comic Sans MS', cursive;
            min-height: 100vh;
            padding: 20px;
        }

        .comic-container {
            max-width: 1000px;
            margin: 40px auto;
            padding: 20px;
        }

        .comic-header {
            text-align: center;
            margin-bottom: 40px;
            animation: fadeIn 1s ease-in;
            background: linear-gradient(135deg, #061c7bff 0%, #d7aeffff 100%);
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .comic-header h1 {
            font-size: 48px;
            color: white;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            margin-bottom: 10px;
            letter-spacing: 2px;
        }

        .comic-header p {
            font-size: 18px;
            color: white;
            font-style: italic;
        }

        .comic-page {
            display: none;
            animation: slideIn 0.5s ease-out;
            min-height: 600px;
        }

        .comic-page.active {
            display: block;
        }

        .comic-panel {
            background: #2C3E50;
            border: 3px solid #34495e;
            border-radius: 15px;
            padding: 30px;
            margin: 20px 0;
            box-shadow: 8px 8px 0px rgba(0, 0, 0, 0.3);
            position: relative;
        }

        .comic-panel::before {
            content: '';
            position: absolute;
            top: -15px;
            right: -15px;
            width: 30px;
            height: 30px;
            background: #4a9eff;
            border-radius: 50%;
            border: 3px solid #34495e;
        }

        .comic-panel h2 {
            color: #4a9eff;
            font-size: 32px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 0px rgba(0,0,0,0.5);
        }

        .comic-panel h3 {
            color: #fff;
            font-size: 24px;
            margin: 20px 0 10px 0;
        }

        .comic-panel p {
            color: #ccc;
            line-height: 1.8;
            font-size: 16px;
            margin-bottom: 15px;
        }

        /* responsive images used inside the comic panels */
        .comic-image {
            max-width: 100%;
            height: auto;
            display: block;
            margin-top: 20px;
            border-radius: 8px;
        }

        .commit-card {
            background: #1e5287;
            border: 4px solid #4a9eff;
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 6px 6px 0px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease;
        }

        .commit-card:hover {
            transform: translateY(-5px);
            box-shadow: 8px 8px 0px rgba(0, 0, 0, 0.4);
        }

        .commit-card h4 {
            color: #4a9eff;
            font-size: 22px;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }

        .commit-card .commit-hash {
            background: rgba(0,0,0,0.3);
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 14px;
            color: #2ea44f;
            margin-left: 10px;
            font-family: monospace;
        }

        .commit-card .commit-date {
            color: #999;
            font-size: 14px;
            margin-bottom: 10px;
        }

        .commit-card .commit-description {
            color: #ccc;
            line-height: 1.6;
            margin: 10px 0;
        }

        .commit-card .commit-impact {
            background: rgba(0,0,0,0.2);
            border-left: 4px solid #2ea44f;
            padding: 12px;
            margin-top: 15px;
            border-radius: 5px;
        }

        .commit-card .commit-impact strong {
            color: #2ea44f;
        }

        .collaboration-box {
            background: #1e5287;
            border: 4px solid #4a9eff;
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 6px 6px 0px rgba(0, 0, 0, 0.3);
        }

        .collaboration-box h3 {
            color: #4a9eff;
            font-size: 28px;
            margin-bottom: 15px;
            text-shadow: 2px 2px 0px rgba(0,0,0,0.5);
        }

        .collab-principle {
            background: rgba(0,0,0,0.3);
            border-radius: 10px;
            padding: 15px;
            margin: 15px 0;
            border-left: 5px solid #4a9eff;
        }

        .collab-principle strong {
            color: #4a9eff;
            font-size: 18px;
            display: block;
            margin-bottom: 8px;
        }

        .collab-principle p {
            color: #ccc;
            line-height: 1.6;
        }

        .best-practice {
            background: #1a7f37;
            border: 3px solid #2ea44f;
            border-radius: 10px;
            padding: 20px;
            margin: 15px 0;
            color: #fff;
        }

        .best-practice h4 {
            color: #fff;
            margin-bottom: 10px;
            font-size: 20px;
        }

        .best-practice ul {
            margin-left: 20px;
            color: #a8e6cf;
        }

        .best-practice li {
            margin: 8px 0;
        }

        .anti-pattern {
            background: #9B3434;
            border: 3px solid #c24444;
            border-radius: 10px;
            padding: 20px;
            margin: 15px 0;
            color: #fff;
        }

        .anti-pattern h4 {
            color: #fff;
            margin-bottom: 10px;
            font-size: 20px;
        }

        .anti-pattern ul {
            margin-left: 20px;
            color: #ffcccc;
        }

        .anti-pattern li {
            margin: 8px 0;
        }

        .navigation {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 40px;
            padding: 20px;
            gap: 12px;
        }

        .nav-button {
            background: #374151;
            color: #fff;
            border: 1px solid #4b5563;
            border-radius: 8px;
            padding: 10px 20px;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.2s ease;
            font-family: inherit;
        }

        .nav-button:hover:not(:disabled) {
            background: #1f2937;
            transform: translateY(-1px);
        }

        .nav-button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .page-indicator {
            background: #1f2937;
            color: #fff;
            border: 1px solid #374151;
            border-radius: 8px;
            padding: 8px 16px;
            font-size: 14px;
            font-weight: 500;
        }

        @media (max-width: 768px) {
            .comic-header h1 {
                font-size: 32px;
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideIn {
            from { 
                opacity: 0;
                transform: translateX(50px);
            }
            to { 
                opacity: 1;
                transform: translateX(0);
            }
        }
    </style>
</head>
<body>
    <div class="comic-container">
        <div class="comic-header">
            <h1> My Development Journey</h1>
            <p>Official Commits & Collaboration Insights</p>
        </div>
        <!-- Page 1: My Official Commits -->
        <div class="comic-page active" id="page-1">
            <div class="comic-panel">
                <h2> My Official Commits</h2>
                <p>A showcase of my contributions to real-world projects, demonstrating technical growth and problem-solving abilities.</p>
                <img src="{{site.baseurl}}/images/FinalReview/image(1).png" alt="tools" class="comic-image" />
            </div>
            <div class="commit-card">
                <h4>
                    Feature: SCSS/CSS Additions
                    <span class="commit-hash">#a7f3c2d</span>
                </h4>
                <div class="commit-date">📅 August 25, 2025</div>
                <div class="commit-description">
                    <section>
                <ul>
                    <li>Created new <code>rps_lesson.scss</code> file with extensive styling for a Rock Paper Scissors lesson page</li>
                    <li>Added import for the new RPS lesson styles in <code>_main.scss</code></li>
                    <li>Generated compiled CSS files (<code>rps_lesson.css</code> and <code>rps_lesson.css.map</code>)</li>
                    <li>Styling includes:
                    <ul>
                        <li>Gradient backgrounds (blue/purple theme)</li>
                        <li>Custom button styles with hover effects</li>
                        <li>Console and code block styling</li>
                        <li>Section highlighting and phase sections</li>
                        <li>Game area styling with positioned elements</li>
                        <li>Responsive container layout with gold borders</li>
                        <li>Multiple heading styles with different colors</li>
                    </ul>
                    </li>
                </ul>
                </section>

                <section>
                <h2>Markdown File</h2>
                <p>
                    Modified <code>agile_rock_paper_scissors.md</code> 
                    (246 additions, 306 deletions)
                </p>
                <p>
                    This appears to be a significant rewrite/restructuring of the Rock Paper Scissors lesson content.
                </p>
                </section>

                </div>
                <div class="commit-impact">
                    <strong>Impact:</strong> Adding a .scss file is important because it lets you write cleaner, more organized, and more powerful styles using variables, nesting, mixins, and reusable components that regular CSS can’t provide. By compiling SCSS into CSS, your project stays efficient and scalable while keeping styles easy to maintain. It also allows you to separate page-specific or feature-specific styles without cluttering your main stylesheet.
                </div>
            </div>

            <div class="commit-card">
                <h4>
                    Fix: Dating Website
                    <span class="commit-hash">#b9e4d1f</span>
                </h4>
                <div class="commit-date">📅 October 12, 2025</div>
                <div class="commit-description">
                    <section>
                    <h4>Backend Changes </h4>

                    <h4>MBTI Support Added:</h4>
                    <ul>
                        <li>Added <code>mbti</code> field to all celebrity profiles (ENFP, ESTP, INFJ, ISFJ, INTJ)</li>
                        <li>Enhanced <code>compute_score()</code> function to accept optional MBTI parameters</li>
                        <li>Created new <code>mbti_similarity_bonus()</code> function that:
                        <ul>
                            <li>Awards 15 points for identical MBTI types</li>
                            <li>Awards 3 points per matching letter in different types</li>
                        </ul>
                        </li>
                        <li>Updated user storage to include MBTI type</li>
                        <li>Modified all API endpoints to accept and process MBTI data:
                        <ul>
                            <li><code>/api/match-user</code> – now accepts <code>mbti</code> parameter</li>
                            <li><code>/api/compatibility</code> – now accepts <code>mbti1</code> and <code>mbti2</code> parameters</li>
                        </ul>
                        </li>
                    </ul>
                    </section>

                    <section>
                    <h4>Frontend Changes </h4>

                    <h4>New Personality Quiz Section:</h4>
                    <ul>
                        <li>Added 5-question MBTI assessment covering all four dimensions:
                        <ul>
                            <li>Extraversion vs Introversion (2 questions)</li>
                            <li>Sensing vs Intuition</li>
                            <li>Thinking vs Feeling</li>
                            <li>Judging vs Perceiving</li>
                        </ul>
                        </li>
                        <li>Quiz calculates estimated MBTI type and auto-fills it into the main form</li>
                        <li>Stores result in <code>localStorage</code> for persistence</li>
                    </ul>

                    <h3>Enhanced User Experience:</h3>
                    <ul>
                        <li>Added MBTI dropdown with all 16 personality types</li>
                        <li>Updated all form validations to require MBTI input</li>
                        <li>Modified API calls to include MBTI data</li>
                        <li>Enhanced result displays to show MBTI types for matches</li>
                        <li>Updated previous users dropdown to show MBTI information</li>
                        <li>Added user's own MBTI to match results display</li>
                    </ul>
                    </section>

                    <section>
                    <h2>Overall Impact</h2>
                    <p>
                        These changes transformed the system from a basic interest-based matcher into a 
                        personality-driven compatibility calculator that considers both user interests and 
                        psychological type alignment.
                    </p>
                    </section>

                </div>
                <div class="commit-impact">
                    <strong> ✅ Impact of the MBTI Changes on API Calls:</strong> Adding MBTI support transformed the API from a simple name/interest matcher into a multi-factor compatibility system. By introducing new MBTI fields and requiring them in the requests, each endpoint now processes more detailed psychological data, leading to more accurate and personalized match results.
                </div>
            </div>

            <div class="commit-card">
                <h4>
                    Enhancement: API Response Caching
                    <span class="commit-hash">#c3f8e2a</span>
                </h4>
                <div class="commit-date">📅 October 8-9, 2025</div>
                <div class="commit-description">
                    <section>
                    <h2>Lesson Structure & Content Creation</h2>
                    <p><strong>Topic:</strong> Unit 1.8 - Documentation in Java</p>
                    <p>You created a comprehensive Jupyter notebook lesson covering:</p>
                    <ul>
                        <li><strong>Why Documentation Matters:</strong> Explaining the audience (developers, maintainers, users) and purpose</li>
                        <li><strong>Javadoc Comment Structure:</strong> Teaching the <code>/** */</code> syntax and tags like <code>@param</code>, <code>@return</code>, <code>@throws</code></li>
                        <li><strong>Preconditions and Postconditions:</strong> Explaining contract programming concepts</li>
                        <li><strong>Class-Level Documentation:</strong> How to document entire classes</li>
                        <li><strong>Documentation Best Practices:</strong> DO's and DON'Ts with examples</li>
                        <li><strong>AP Exam Connections:</strong> Relating content to AP Computer Science A exam</li>
                        <li><strong>Hands-on Hacks:</strong> Practice exercises for students</li>
                        <li><strong>Homework Assignment:</strong> Extended practice problems</li>
                        <li><strong>Challenge Problems:</strong> Extra credit opportunities</li>
                    </ul>
                    </section>

                    <section>
                    <h2>Your Bug Fixes (Commit 2410b67)</h2>

                    <h3>1. Fixed the <code>withdraw()</code> Method (Lines 165-254)</h3>
                    <p><strong>Problems you solved:</strong></p>
                    <ul>
                        <li>Method was incomplete with undefined <code>recordTransaction()</code> function</li>
                        <li>No actual working code to demonstrate the concept</li>
                    </ul>
                    <p><strong>Your fixes:</strong></p>
                    <ul>
                        <li>Added local variables (<code>balance = 500.0</code>, <code>isFrozen = false</code>) to make it executable</li>
                        <li>Replaced <code>recordTransaction()</code> with simple <code>System.out.println()</code> statements</li>
                        <li>Made the method runnable by adding <code>withdraw(100.0);</code> test call</li>
                        <li>Added clear console output showing transaction details and new balance</li>
                        <li>Kept all the documentation intact while making the code functional</li>
                    </ul>

                    <h3>2. Completed the Student Class (Lines 222-296)</h3>
                    <p><strong>Problems you solved:</strong></p>
                    <ul>
                        <li>Class was just a skeleton with no implementation</li>
                        <li>Comment said "Constructor and methods..." but nothing was there</li>
                    </ul>
                    <p><strong>Your fixes:</strong></p>
                    <ul>
                        <li>Added working constructor that initializes all instance variables</li>
                        <li>Implemented <code>enrollInCourse()</code> - adds courses to <code>ArrayList</code></li>
                        <li>Implemented <code>updateGrade()</code> - stores grades in <code>HashMap</code></li>
                        <li>Implemented <code>getGPA()</code> - calculates average grade with proper error handling for empty grades</li>
                        <li>Added test code creating a Student object and demonstrating all methods</li>
                        <li>Made the example actually output <code>95.5</code> to show it works</li>
                    </ul>

                    <h3>3. Updated Execution Counts</h3>
                    <p>Changed cells from <code>execution_count: null</code> to actual numbers (8, 15, 17, 18) to show you ran and tested all code cells.</p>
                    </section>

                    <section>
                    <h2>Teaching Approach</h2>
                    <p> built this as an executable, interactive lesson where:</p>
                    <ul>
                        <li>Students can read the theory</li>
                        <li>See real, working code examples</li>
                        <li>Run the code themselves in Jupyter</li>
                        <li>Practice with hands-on hacks</li>
                        <li>Learn AP exam-specific skills</li>
                    </ul>
                    <p>The fixes transformed non-functional placeholder code into working demonstrations that students can actually execute and learn from. This is crucial for a coding lesson—students need to see working examples, not just commented skeletons.</p>
                    </section>

                </div>
                <div class="commit-impact">
                    <strong>Impact:</strong> The lesson first establishes why documentation matters, showing its real-world relevance for developers, maintainers, and users, and then teaches the how with Javadoc syntax, pre/postconditions, and class-level documentation. Best practices and AP exam connections ensure students understand quality standards and can directly apply the concepts to exam-style problems. The hacks and homework sections transform theory into active learning, giving students scaffolded exercises, immediate feedback, and real-world practice that builds skill, confidence, and retention
                </div>
            </div>

            <div class="commit-card">
                <h4>
                    Refactor: Authentication Module
                    <span class="commit-hash">#d5a2f3b</span>
                </h4>
                <div class="commit-date"> OTHER</div>
                <div class="commit-description">
                   <img src="{{site.baseurl}}/images/FinalReview/image2.png" alt="tools" class="comic-image" />
                </div>
                <div class="commit-impact">
                    <strong>Impact:</strong> Debugging ensures that code runs correctly, turning non-functional or incomplete examples into working, testable programs. It also helps students understand logic, catch errors early, and learn best practices through hands-on problem-solving.
                </div>
            </div>
        </div>
<div class="comic-panel">
                <h3> Lessons Learned</h3>
                <p><strong>Collaboration isn't just about code—it's about people.</strong> The best technical solution means nothing if your team can't understand, maintain, or build upon it. Invest in communication, documentation, and relationships as much as you invest in technical skills.</p>
                
                <p style="margin-top: 20px;"><strong>Embrace feedback.</strong> Every bug report, code review comment, and architectural discussion is an opportunity to grow. The developers who advance fastest are those who seek feedback actively and implement it graciously.</p>

                <p style="margin-top: 20px;"><strong>Balance speed with quality.</strong> Move fast, but not so fast that you create technical debt for others. Good collaboration means considering the long-term impact of your code on the team and the product.</p>
            </div>

            <div class="collaboration-box" style="margin-top: 40px;">
                <h3> My Collaboration Journey</h3>
                
                <div class="collab-principle">
                    <strong>Cross-Team Code Reviews & Issue Creation</strong>
                    <p>On the Root Color Map project, I created a detailed pull request and collaborated with Ahan and Nickel's team to ensure smooth integration. I also worked remotely with Ansh's team, creating a comprehensive issue that clearly outlined the requirements and changes needed. This experience taught me the importance of clear documentation—when working across teams, well-structured issues and PRs bridge the gap between different working styles and timelines.</p>
                </div>

                <div class="collab-principle">
                    <strong>Leading Educational Content & Peer Grading</strong>
                    <p>I took on a significant role in creating and grading lessons, ensuring consistent follow-up on homework assignments and engaging in discussions with peers about their work. For the Rock, Paper, Scissors lesson, I collaborated with both CSP and CSSE students, grading their submissions and providing constructive feedback. This dual role of teacher and collaborator deepened my understanding—explaining concepts to others reinforced my own knowledge while helping the community grow together.</p>
                </div>

                <div class="collab-principle">
                    <strong>Night at the Museum Project</strong>
                    <p>During our group's Night of the Museum project, I worked extensively on submodule three, focusing on the prompting system and creating an interactive user experience with a progress bar. Before the merge, I ensured the feature was polished and user-friendly. At the NTVM event itself, I engaged with three CSP groups, leaving detailed comments on two projects and learning about their creative approaches to illustrating different locations, activities, and sports. This experience highlighted how presenting your work and receiving immediate feedback creates a powerful learning loop.</p>
                </div>

                <div class="collab-principle">
                    <strong>Dating Website Development & Iteration</strong>
                    <p>I contributed to the dating website project through active discussion and implementation work, maintaining open communication channels throughout development. This project required balancing multiple perspectives and requirements, teaching me how to negotiate features and prioritize user experience in a collaborative setting.</p>
                </div>

                <div class="collab-principle">
                    <strong>Seeking Mentorship & External Review</strong>
                    <p>For the Rock, Paper, Scissors project, I proactively approached Mr. Mortensen to discuss our lesson page structure and Sass file organization. I also reached out to Avika's group for CSS and styling advice, and engaged in cross-reviews with their team. Working with Risha's team, I sought guidance on both project architecture and personal blog improvements, even creating formal issues to track our discussions. Additionally, I collaborated with Rohan's group regarding lesson format and best practices. These experiences taught me that asking for help isn't weakness—it's strategic learning.</p>
                </div>

                <div class="collab-principle">
                    <strong>Iterative Review & Continuous Improvement</strong>
                    <p>Throughout the year, I participated in multiple review cycles for our Rock, Paper, Scissors project as part of a trio team. We regularly reviewed each other's code, identified improvements, and iterated on our design. This consistent practice of peer review built a culture of quality and continuous improvement within our team, showing me that great software isn't written once—it's refined through collaborative iteration.</p>
                </div>
            </div>

            <div class="best-practice" style="margin-top: 30px;">
                <h4> Key Takeaways from Real Collaboration</h4>
                <ul>
                    <li><strong>Documentation Drives Success:</strong> Clear issues and PR descriptions enabled seamless cross-team collaboration on Root Color Map</li>
                    <li><strong>Teaching Reinforces Learning:</strong> Grading lessons and helping peers solidified my own understanding of concepts</li>
                    <li><strong>Ask Questions Early:</strong> Reaching out to Mr. Mortensen and experienced peers saved hours of debugging</li>
                    <li><strong>Cross-Pollination of Ideas:</strong> Reviewing other teams' CSS approaches and getting their feedback improved our own work</li>
                    <li><strong>In-Person Feedback is Invaluable:</strong> NTVM conversations provided insights that online comments couldn't capture</li>
                    <li><strong>Iteration Over Perfection:</strong> Multiple review cycles produced better results than trying to get it right the first time</li>
                </ul>
            </div>
    <script>
        let currentPage = 1;
        const totalPages = 2;

        function changePage(direction) {
            const newPage = currentPage + direction;
            
            if (newPage < 1 || newPage > totalPages) {
                return;
            }

            document.getElementById(`page-${currentPage}`).classList.remove('active');
            currentPage = newPage;
            document.getElementById(`page-${currentPage}`).classList.add('active');
            
            document.getElementById('current-page').textContent = currentPage;
            
            document.getElementById('prev-btn').disabled = currentPage === 1;
            document.getElementById('next-btn').disabled = currentPage === totalPages;
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    </script>
</html>