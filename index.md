<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Pacifico&family=Indie+Flower&display=swap">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <title>Ali Nikkhah Portfolio</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #333;
            color: #fff;
            padding: 10px 20px;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }
        header h1 {
            font-family: 'Pacifico', cursive;
        }
        .menu-icon {
            display: none;
            cursor: pointer;
        }
        nav {
            display: flex;
        }
        nav ul {
            display: flex;
            list-style: none;
            margin: 0;
            padding: 0;
        }
        nav ul li {
            margin: 0 10px;
        }
        nav ul li a {
            color: #fff;
            text-decoration: none;
            font-weight: bold;
        }
        @media (max-width: 768px) {
            nav {
                display: none;
                flex-direction: column;
                background: #444;
                position: absolute;
                top: 60px;
                right: 0;
                width: 200px;
                border-radius: 5px;
            }
            nav ul {
                flex-direction: column;
            }
            nav ul li {
                margin: 10px;
            }
            .menu-icon {
                display: block;
            }
        }
        main {
            padding: 80px 20px;
            max-width: 800px;
            margin: auto;
        }
        h1, h2, h3, h4, h5 {
            margin-bottom: 10px;
        }
        h1 {
            font-size: 2.5rem;
        }
        h2 {
            font-size: 2rem;
        }
        h3 {
            font-size: 1.75rem;
        }
        h4 {
            font-size: 1.5rem;
        }
        h5 {
            font-size: 1.25rem;
        }
        blockquote {
            font-family: 'Indie Flower', cursive;
            font-size: 1.5rem;
            background: #f9f9f9;
            border-left: 10px solid #ccc;
            padding: 10px 20px;
            margin: 20px 0;
        }
        img {
            max-width: 100%;
            height: auto;
        }
        ul {
            list-style: disc;
            padding-left: 20px;
        }
        a {
            color: #007bff;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
    </style>
    <script>
        function toggleMenu() {
            const nav = document.querySelector('nav');
            nav.style.display = nav.style.display === 'flex' ? 'none' : 'flex';
        }
    </script>
</head>
<body>
    <header>
        <h1>Ali Nikkhah</h1>
        <div class="menu-icon" onclick="toggleMenu()">
            <i class="fas fa-bars"></i>
        </div>
        <nav>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">About</a></li>
                <li><a href="#">Portfolio</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <blockquote>
            "Stay Hungry, Stay Foolish"<br>
            <span>&mdash; <em>Steve Jobs</em></span>
        </blockquote>
        <h2>Academic Study</h2>
        <h3>Education</h3>
        <ul>
            <li><strong>Sharif University of Technology</strong> (Sep 2020 - Present)<br>
                Bachelor’s in Electrical Engineering<br>
                <strong>Specialization:</strong> Digital Systems<br>
                <strong>GPA:</strong> 3.85
            </li>
        </ul>
        <h2>Certificates</h2>
        <h3>Self-Study Courses</h3>
        <ul>
            <li>Parallel Programming and Big Data Analysis (EPFL)</li>
            <li>Machine Learning Specialization (DeepLearning.ai)</li>
            <li>Deep Learning Specialization (DeepLearning.ai)</li>
            <li>MLOps Specialization (DeepLearning.ai)</li>
            <li>Introduction to Self-Driving Cars (University of Toronto)</li>
            <li>Mathematical Concepts of Machine Learning (Imperial College London)</li>
        </ul>
        <p>Full list of certificates can be found on my <a href="https://www.linkedin.com/in/alinikkhah2001">LinkedIn page</a>.</p>
        <h2>Work Experience</h2>
        <h3>Software Engineer</h3>
        <p><strong>Homa Cloud</strong> (Machine Learning Researcher/Developer)</p>
        <ul>
            <li>Specialized in distributed machine learning using tools like TensorFlow Distributed, Horovod, and Spark.</li>
            <li>Optimized multi-node, multi-GPU training for scalability and resource efficiency.</li>
            <li>Leveraged Scala and Spark for efficient data processing and multi-node model evaluations.</li>
        </ul>
        <h2>Research Experience</h2>
        <h3>Spread Time CDMA Transceiver</h3>
        <p><strong>Sharif University of Technology</strong> (Undergraduate Research Assistant)</p>
        <ul>
            <li>Developed a communication technique combining TDMA and CDMA.</li>
            <li>Focused on mathematical modeling, data analysis, and ASIC design.</li>
            <li>Designed flexible FFT/IFFT butterfly modules under the guidance of Dr. Noyan Akbar.</li>
        </ul>
        <h2>Teaching Experience</h2>
        <ul>
            <li><strong>Circuit Theory (1, 2)</strong><br>Head of TA Team: Held tutorials and designed homework questions.</li>
            <li><strong>Analog Electronics (1, 2, 3)</strong><br>Conducted tutorials and created homework assignments.</li>
            <li><strong>Engineering Probability, Statistics, and Random Processes</strong><br>Designed challenging homework questions.</li>
        </ul>
        <h2>Projects</h2>
        <h3>Generative Models</h3>
        <p>Developed models like GANs, VAEs, and Diffusion Models. Achieved efficient representation learning using hierarchical encoder-decoder architectures.</p>
        <h3>Sentiment Analysis</h3>
        <p>Analyzed tweet sentiments and financial data using LSTMs and fine-tuning techniques.</p>
        <h3>Flexible Image Classification</h3>
        <p>Designed models with deformable convolutions for handling image distortions.</p>
        <h3>GANBERT</h3>
        <p>Combined GANs and BERT for classifying AI-generated vs. human-generated text.</p>
        <h3>FPGA Line Detection</h3>
        <p>Implemented the Sobel Kernel algorithm for real-time image processing on FPGA.</p>
        <p>Explore my full list of projects on my <a href="https://github.com/alinikkhah2001">GitHub page</a>.</p>
        <h2>Skills</h2>
        <h3>Hardware Design</h3>
        <ul>
            <li>Verilog, VHDL, LTSpice, HSpice, Pspice, Matlab</li>
        </ul>
        <h3>Programming Languages</h3>
        <ul>
            <li>Python, Django, Java, Node.js, C++, C, R</li>
        </ul>
        <h3>Deep Learning Frameworks</h3>
        <ul>
            <li>PyTorch, TensorFlow, Keras, Hugging Face, OpenCV</li>
        </ul>
        <h3>Data Science Tools</h3>
        <ul>
            <li>Pandas, Numpy, Scikit-Learn, Spark, Scala</li>
        </ul>
        <h3>Visualization Tools</h3>
        <ul>
            <li>Tableau, Metabase, Grafana, TensorBoard</li>
        </ul>
        <h3>CI/CD & Orchestration</h3>
        <ul>
            <li>Docker, Kubernetes, GitLab CI/CD</li>
        </ul>
        <h2>Courses</h2>
        <h3>University Courses</h3>
        <ul>
            <li>Deep Learning, Machine Learning, Generative Models, NLP</li>
            <li>ASIC-FPGA, Analog Electronics, VLSI, Embedded Systems</li>
        </ul>
        <h2>Interests</h2>
        <ul>
            <li>Computer Vision, Generative Models, Natural Language Processing</li>
            <li>VLSI, Embedded Systems, IoT</li>
        </ul>
        <h3>Connect with me on</h3>
        <p>
            📧 <strong>Email</strong>: <a href="mailto:alinkkh9@gmail.com">alinkkh9@gmail.com</a><br>
            🔗 <strong>GitHub</strong>: <a href="https://github.com/alinikkhah2001">github.com/alinikkhah2001</a><br>
            🔗 <strong>LinkedIn</strong>: <a href="https://www.linkedin.com/in/alinikkhah2001">linkedin.com/in/alinikkhah2001</a><br>
            🌐 <strong>Personal Webpage</strong>: <a href="http://alinikkhah.ir">alinikkhah.ir</a>
        </p>
    </main>
</body>
</html>
