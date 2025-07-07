import React, { useState, useEffect } from 'react';
import { Github, Mail, Linkedin, Twitter, Code, Database, Cloud, Zap, Star, ExternalLink, Coffee } from 'lucide-react';

const Portfolio = () => {
  const [currentText, setCurrentText] = useState(0);
  const [activeSection, setActiveSection] = useState('about');

  const typingTexts = [
    "Hello World! 👋",
    "I am Sholingaram Hemanth",
    "Full Stack Developer",
    "Code is Poetry 🎨",
    "Building Tomorrow Today 🚀"
  ];

  const featuredProjects = [
    {
      title: "🔐 Secure Authentication System",
      tech: ["Node.js", "MySQL", "JWT"],
      description: "A robust full-stack authentication system with advanced security features",
      status: "Active",
      progress: 85
    },
    {
      title: "🤖 Human-Following Robot",
      tech: ["MediaPipe", "Computer Vision", "Python"],
      description: "Real-time pose estimation robot with human tracking capabilities",
      status: "Development",
      progress: 70
    },
    {
      title: "🧠 AI Resume Analyzer",
      tech: ["NLP", "Python", "Machine Learning"],
      description: "AI-powered resume analyzer using cosine similarity and natural language processing",
      status: "Upcoming",
      progress: 25
    }
  ];

  const topSkills = [
    { name: "JavaScript", level: 95, color: "from-yellow-400 to-orange-500" },
    { name: "React", level: 90, color: "from-blue-400 to-cyan-500" },
    { name: "Node.js", level: 90, color: "from-green-500 to-green-600" },
    { name: "Python", level: 85, color: "from-blue-500 to-indigo-600" },
    { name: "MongoDB", level: 85, color: "from-green-600 to-green-700" },
    { name: "Docker", level: 75, color: "from-blue-500 to-blue-600" }
  ];

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentText((prev) => (prev + 1) % typingTexts.length);
    }, 2500);
    return () => clearInterval(interval);
  }, []);

  const SkillBar = ({ skill }) => (
    <div className="mb-4 group">
      <div className="flex justify-between items-center mb-2">
        <span className="text-sm font-medium text-gray-300">{skill.name}</span>
        <span className="text-sm text-gray-400">{skill.level}%</span>
      </div>
      <div className="w-full bg-gray-700 rounded-full h-2.5 overflow-hidden">
        <div 
          className={`h-2.5 bg-gradient-to-r ${skill.color} rounded-full transition-all duration-1000 ease-out transform group-hover:scale-105`}
          style={{ width: `${skill.level}%` }}
        />
      </div>
    </div>
  );

  const ProjectCard = ({ project }) => (
    <div className="bg-gray-800 bg-opacity-70 rounded-xl p-6 border border-gray-700 hover:border-purple-500 transition-all duration-300 hover:shadow-lg hover:shadow-purple-500/20 transform hover:-translate-y-1 backdrop-blur-sm">
      <div className="flex justify-between items-start mb-3">
        <h3 className="text-lg font-semibold text-white">{project.title}</h3>
        <span className={`px-3 py-1 rounded-full text-xs font-medium ${
          project.status === 'Active' ? 'bg-green-900 text-green-300' :
          project.status === 'Development' ? 'bg-blue-900 text-blue-300' :
          'bg-yellow-900 text-yellow-300'
        }`}>
          {project.status}
        </span>
      </div>
      
      <p className="text-gray-300 text-sm mb-4">{project.description}</p>
      
      <div className="flex flex-wrap gap-2 mb-4">
        {project.tech.map((tech, idx) => (
          <span key={idx} className="px-2 py-1 bg-purple-900 bg-opacity-50 text-purple-300 rounded-full text-xs border border-purple-700">
            {tech}
          </span>
        ))}
      </div>
      
      <div className="mb-4">
        <div className="flex justify-between items-center mb-1">
          <span className="text-xs text-gray-400">Progress</span>
          <span className="text-xs text-gray-400">{project.progress}%</span>
        </div>
        <div className="w-full bg-gray-700 rounded-full h-2">
          <div 
            className="h-2 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full transition-all duration-1000"
            style={{ width: `${project.progress}%` }}
          />
        </div>
      </div>
      
      <div className="flex justify-between items-center">
        <button className="flex items-center gap-2 text-purple-400 hover:text-purple-300 transition-colors text-sm">
          <Github size={16} />
          View Code
        </button>
        <button className="flex items-center gap-2 text-blue-400 hover:text-blue-300 transition-colors text-sm">
          <ExternalLink size={16} />
          Live Demo
        </button>
      </div>
    </div>
  );

  const NavButton = ({ section, icon: Icon, label }) => (
    <button
      onClick={() => setActiveSection(section)}
      className={`flex items-center gap-2 px-4 py-2 rounded-lg transition-all duration-300 ${
        activeSection === section
          ? 'bg-purple-600 text-white shadow-lg shadow-purple-500/30'
          : 'bg-gray-700 text-gray-300 hover:bg-gray-600'
      }`}
    >
      <Icon size={18} />
      <span className="hidden sm:inline">{label}</span>
    </button>
  );

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 via-purple-900 to-gray-900 text-white">
      {/* Animated Background */}
      <div className="fixed inset-0 z-0">
        <div className="absolute inset-0 bg-[radial-gradient(circle_at_30%_40%,rgba(120,119,198,0.2),transparent)] animate-pulse" />
        <div className="absolute inset-0 bg-[radial-gradient(circle_at_70%_70%,rgba(255,119,198,0.2),transparent)] animate-pulse" style={{ animationDelay: '1s' }} />
      </div>

      <div className="relative z-10">
        {/* Header */}
        <header className="container mx-auto px-4 py-8 text-center">
          <h1 className="text-4xl md:text-6xl font-bold bg-gradient-to-r from-purple-400 via-pink-400 to-blue-400 bg-clip-text text-transparent mb-4">
            SHOLINGARAM HEMANTH
          </h1>
          <p className="text-lg text-gray-300 mb-6">
            Full Stack Developer | Code Architect | Digital Innovator
          </p>
          <div className="h-12 flex items-center justify-center">
            <div className="text-xl md:text-2xl font-mono text-purple-400 animate-pulse">
              {typingTexts[currentText]}
            </div>
          </div>
        </header>

        {/* Navigation */}
        <nav className="container mx-auto px-4 mb-8">
          <div className="flex justify-center gap-2 md:gap-4 flex-wrap">
            <NavButton section="about" icon={Code} label="About" />
            <NavButton section="projects" icon={Star} label="Projects" />
            <NavButton section="skills" icon={Zap} label="Skills" />
            <NavButton section="contact" icon={Mail} label="Contact" />
          </div>
        </nav>

        {/* Content Sections */}
        <main className="container mx-auto px-4 pb-8">
          {/* About Section */}
          {activeSection === 'about' && (
            <section className="animate-fadeIn">
              <div className="bg-gray-800 bg-opacity-50 rounded-xl p-6 md:p-8 backdrop-blur-sm border border-gray-700">
                <h2 className="text-2xl md:text-3xl font-bold mb-6 text-center">
                  <span className="bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
                    About The Code Architect
                  </span>
                </h2>
                
                <div className="bg-gray-900 rounded-lg p-4 md:p-6 font-mono text-sm mb-6 overflow-x-auto">
                  <div className="text-blue-400">const</div>
                  <div className="text-yellow-400 ml-4">sholingaramHemanth = {`{`}</div>
                  <div className="ml-8 text-gray-300">
                    <div><span className="text-red-400">location:</span> <span className="text-green-400">"India 🇮🇳"</span>,</div>
                    <div><span className="text-red-400">code:</span> <span className="text-green-400">["JavaScript", "Python", "Java", "TypeScript"]</span>,</div>
                    <div><span className="text-red-400">currentFocus:</span> <span className="text-green-400">"Building awesome web applications 🚀"</span>,</div>
                    <div><span className="text-red-400">funFact:</span> <span className="text-green-400">"I debug with console.log and I am not ashamed 😄"</span></div>
                  </div>
                  <div className="text-yellow-400">{`};`}</div>
                </div>

                <div className="grid md:grid-cols-3 gap-4 text-center">
                  <div className="bg-gradient-to-r from-purple-600 to-purple-700 p-4 rounded-lg">
                    <div className="text-2xl font-bold">25+</div>
                    <div className="text-sm opacity-90">Projects</div>
                  </div>
                  <div className="bg-gradient-to-r from-blue-600 to-blue-700 p-4 rounded-lg">
                    <div className="text-2xl font-bold">500+</div>
                    <div className="text-sm opacity-90">Commits</div>
                  </div>
                  <div className="bg-gradient-to-r from-green-600 to-green-700 p-4 rounded-lg">
                    <div className="text-2xl font-bold">3+</div>
                    <div className="text-sm opacity-90">Years Coding</div>
                  </div>
                </div>
              </div>
            </section>
          )}

          {/* Projects Section */}
          {activeSection === 'projects' && (
            <section className="animate-fadeIn">
              <h2 className="text-2xl md:text-3xl font-bold mb-8 text-center">
                <span className="bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
                  🚀 Featured Projects
                </span>
              </h2>
              <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                {featuredProjects.map((project, idx) => (
                  <ProjectCard key={idx} project={project} />
                ))}
              </div>
            </section>
          )}

          {/* Skills Section */}
          {activeSection === 'skills' && (
            <section className="animate-fadeIn">
              <h2 className="text-2xl md:text-3xl font-bold mb-8 text-center">
                <span className="bg-gradient-to-r from-green-400 to-blue-400 bg-clip-text text-transparent">
                  💻 Core Technologies
                </span>
              </h2>
              <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                {topSkills.map((skill, idx) => (
                  <div key={idx} className="bg-gray-800 bg-opacity-50 rounded-xl p-6 border border-gray-700 backdrop-blur-sm">
                    <SkillBar skill={skill} />
                  </div>
                ))}
              </div>
              
              <div className="mt-8 text-center">
                <div className="bg-gray-800 bg-opacity-50 rounded-xl p-6 border border-gray-700 backdrop-blur-sm">
                  <h3 className="text-xl font-semibold mb-4">Currently Learning</h3>
                  <div className="flex flex-wrap justify-center gap-3">
                    {["Next.js", "Docker", "AWS", "GraphQL", "React Native"].map((tech, idx) => (
                      <span key={idx} className="px-3 py-1 bg-yellow-900 bg-opacity-50 text-yellow-300 rounded-full text-sm border border-yellow-700">
                        {tech}
                      </span>
                    ))}
                  </div>
                </div>
              </div>
            </section>
          )}

          {/* Contact Section */}
          {activeSection === 'contact' && (
            <section className="animate-fadeIn">
              <div className="bg-gray-800 bg-opacity-50 rounded-xl p-6 md:p-8 border border-gray-700 backdrop-blur-sm">
                <h2 className="text-2xl md:text-3xl font-bold mb-6 text-center">
                  <span className="bg-gradient-to-r from-pink-400 to-purple-400 bg-clip-text text-transparent">
                    🤝 Let's Connect
                  </span>
                </h2>
                
                <div className="grid md:grid-cols-2 gap-6 mb-8">
                  <div>
                    <h3 className="text-lg font-semibold mb-4">Get in Touch</h3>
                    <div className="space-y-3">
                      <button className="w-full flex items-center gap-3 bg-gradient-to-r from-red-500 to-red-600 px-4 py-3 rounded-lg hover:from-red-600 hover:to-red-700 transition-all duration-300">
                        <Mail size={20} />
                        <span>sholingaramhemanth@gmail.com</span>
                      </button>
                      <button className="w-full flex items-center gap-3 bg-gradient-to-r from-blue-500 to-blue-600 px-4 py-3 rounded-lg hover:from-blue-600 hover:to-blue-700 transition-all duration-300">
                        <Linkedin size={20} />
                        <span>LinkedIn Profile</span>
                      </button>
                      <button className="w-full flex items-center gap-3 bg-gradient-to-r from-gray-700 to-gray-800 px-4 py-3 rounded-lg hover:from-gray-800 hover:to-gray-900 transition-all duration-300">
                        <Github size={20} />
                        <span>GitHub Profile</span>
                      </button>
                    </div>
                  </div>
                  
                  <div>
                    <h3 className="text-lg font-semibold mb-4">Support My Work</h3>
                    <button className="w-full flex items-center justify-center gap-3 bg-gradient-to-r from-yellow-500 to-orange-500 px-4 py-3 rounded-lg hover:from-yellow-600 hover:to-orange-600 transition-all duration-300">
                      <Coffee size={20} />
                      <span>Buy Me A Coffee</span>
                    </button>
                    <p className="text-sm text-gray-400 mt-3 text-center">
                      Help fuel my coding adventures! ☕
                    </p>
                  </div>
                </div>
              </div>
            </section>
          )}
        </main>

        {/* Footer */}
        <footer className="text-center py-6 border-t border-gray-700">
          <p className="text-gray-400 text-sm">
            "Code is like humor. When you have to explain it, it is bad." – Cory House
          </p>
        </footer>
      </div>

      <style jsx>{`
        @keyframes fadeIn {
          from { opacity: 0; transform: translateY(20px); }
          to { opacity: 1; transform: translateY(0); }
        }
        .animate-fadeIn {
          animation: fadeIn 0.5s ease-out;
        }
      `}</style>
    </div>
  );
};

export default Portfolio;
