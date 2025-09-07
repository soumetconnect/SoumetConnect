## Hi there 👋

<!--
**soumetconnect/SoumetConnect** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
import React, { useState, useEffect } from 'react';
import { 
  BookOpen, Sun, Heart, Eye, Volume2, ChevronLeft, ChevronRight, Edit, Save, 
  Calendar, Menu, Clock, Share2, Download, Play, Pause, Video, Facebook, 
  Twitter, Instagram, Youtube, Settings, User, Home, Search, Bell, X, Moon
} from 'lucide-react';

// Digital Clock Component
const DigitalClock = () => {
  const [time, setTime] = useState(new Date());

  useEffect(() => {
    const timer = setInterval(() => {
      setTime(new Date());
    }, 1000);

    return () => clearInterval(timer);
  }, []);

  return (
    <div className="flex items-center text-xs text-blue-200 bg-blue-900/30 border border-blue-500/30 px-3 py-2 rounded-lg backdrop-blur-sm">
      <Clock className="w-3 h-3 mr-2" />
      <div className="font-mono">
        <span className="text-blue-100">
          {time.toLocaleTimeString('en-US', { 
            hour12: false,
            hour: '2-digit',
            minute: '2-digit'
          })}
        </span>
        <span className="ml-2 text-blue-300">
          {time.toLocaleDateString('en-US', { 
            weekday: 'short',
            month: 'short',
            day: 'numeric'
          })}
        </span>
      </div>
    </div>
  );
};

// Theme Toggle Component
const ThemeToggle = ({ isDark, toggleTheme }) => {
  return (
    <button
      onClick={toggleTheme}
      className={`p-2 rounded-lg border transition-all duration-300 ${
        isDark 
          ? 'bg-yellow-500/20 border-yellow-500/30 text-yellow-300 hover:bg-yellow-500/30' 
          : 'bg-gray-700/20 border-gray-500/30 text-gray-400 hover:bg-gray-700/30'
      }`}
    >
      {isDark ? <Sun className="w-4 h-4" /> : <Moon className="w-4 h-4" />}
    </button>
  );
};

// Navigation Menu Component
const NavigationMenu = ({ isOpen, toggleMenu, isDark }) => {
  const bgClass = isDark 
    ? 'bg-black/80 backdrop-blur-xl border-purple-500/40 shadow-purple-500/20' 
    : 'bg-white/90 backdrop-blur-xl border-gray-300 shadow-gray-500/20';
  
  const headerBgClass = isDark 
    ? 'bg-gradient-to-r from-purple-900/40 to-blue-900/40' 
    : 'bg-gradient-to-r from-blue-100 to-purple-100';
  
  const textClass = isDark ? 'text-white' : 'text-gray-800';
  const secondaryTextClass = isDark ? 'text-gray-300' : 'text-gray-600';

  return (
    <>
      {/* Mobile Menu Overlay */}
      {isOpen && (
        <div className="fixed inset-0 bg-black/80 z-40 lg:hidden" onClick={toggleMenu}></div>
      )}
      
      {/* Navigation Menu */}
      <nav className={`fixed top-0 left-0 h-full ${bgClass} z-50 transform transition-transform duration-300 ${
        isOpen ? 'translate-x-0' : '-translate-x-full'
      } lg:relative lg:transform-none lg:w-56 lg:block shadow-2xl`}>
        <div className={`p-4 border-b ${isDark ? 'border-purple-500/40' : 'border-gray-300'} ${headerBgClass} backdrop-blur-sm`}>
          <div className="flex items-center justify-between">
            <div className="flex items-center">
              <div className="w-8 h-8 bg-gradient-to-br from-blue-500 to-purple-600 rounded-lg flex items-center justify-center mr-2 shadow-lg shadow-blue-500/50">
                <BookOpen className="w-4 h-4 text-white" />
              </div>
              <span className={`font-bold ${textClass} text-sm`}>Soumet Connect</span>
            </div>
            <button onClick={toggleMenu} className="lg:hidden">
              <X className={`w-5 h-5 ${secondaryTextClass}`} />
            </button>
          </div>
        </div>
        
        <div className="p-3">
          <div className="space-y-1">
            <button className={`w-full flex items-center px-3 py-2 rounded-lg bg-gradient-to-r from-blue-600/30 to-purple-600/30 border ${isDark ? 'border-blue-500/40 text-blue-200' : 'border-blue-300 text-blue-700'} text-sm shadow-lg shadow-blue-500/20`}>
              <Home className="w-4 h-4 mr-2" />
              Dashboard
            </button>
            <button className={`w-full flex items-center px-3 py-2 rounded-lg ${secondaryTextClass} ${isDark ? 'hover:bg-white/5 hover:text-white hover:border-gray-500/30' : 'hover:bg-gray-100 hover:text-gray-800 hover:border-gray-300'} hover:border transition-all text-sm`}>
              <Search className="w-4 h-4 mr-2" />
              Search Content
            </button>
            <button className={`w-full flex items-center px-3 py-2 rounded-lg ${secondaryTextClass} ${isDark ? 'hover:bg-white/5 hover:text-white hover:border-gray-500/30' : 'hover:bg-gray-100 hover:text-gray-800 hover:border-gray-300'} hover:border transition-all text-sm`}>
              <Bell className="w-4 h-4 mr-2" />
              Notifications
            </button>
            <button className={`w-full flex items-center px-3 py-2 rounded-lg ${secondaryTextClass} ${isDark ? 'hover:bg-white/5 hover:text-white hover:border-gray-500/30' : 'hover:bg-gray-100 hover:text-gray-800 hover:border-gray-300'} hover:border transition-all text-sm`}>
              <User className="w-4 h-4 mr-2" />
              Profile
            </button>
            <button className={`w-full flex items-center px-3 py-2 rounded-lg ${secondaryTextClass} ${isDark ? 'hover:bg-white/5 hover:text-white hover:border-gray-500/30' : 'hover:bg-gray-100 hover:text-gray-800 hover:border-gray-300'} hover:border transition-all text-sm`}>
              <Settings className="w-4 h-4 mr-2" />
              Settings
            </button>
          </div>
        </div>
      </nav>
    </>
  );
};

// Header Component
const Header = ({ isDark, toggleTheme }) => {
  const bgClass = isDark 
    ? 'bg-black/60 backdrop-blur-xl border-blue-500/40 shadow-blue-500/20' 
    : 'bg-white/80 backdrop-blur-xl border-gray-300 shadow-gray-300/20';
  
  const textClass = isDark ? 'text-white' : 'text-gray-800';

  return (
    <header className={`${bgClass} border rounded-xl shadow-2xl mb-6 relative overflow-hidden`}>
      {/* Header Glow Effect */}
      <div className={`absolute inset-0 ${isDark ? 'bg-gradient-to-r from-blue-500/5 via-purple-500/5 to-cyan-500/5' : 'bg-gradient-to-r from-blue-100/50 via-purple-100/50 to-cyan-100/50'}`}></div>
      <div className="relative z-10 p-6">
        <div className="text-center">
          <h1 className="text-3xl font-bold bg-gradient-to-r from-blue-500 via-purple-500 to-cyan-500 bg-clip-text text-transparent mb-2">
            Soumet Connect
          </h1>
          <p className={`text-sm font-medium ${isDark ? 'text-blue-200/80' : 'text-gray-600'}`}>
            Best Spiritual Connectivity Network
          </p>
        </div>
        
        {/* Bottom section with clock and theme toggle */}
        <div className="flex justify-between items-center mt-6">
          <DigitalClock />
          <ThemeToggle isDark={isDark} toggleTheme={toggleTheme} />
        </div>
      </div>
    </header>
  );
};

// Social Media Component
const SocialMedia = ({ isDark }) => {
  const socialLinks = [
    { icon: Facebook, name: 'Facebook', color: 'hover:text-blue-400' },
    { icon: Twitter, name: 'Twitter', color: 'hover:text-sky-400' },
    { icon: Instagram, name: 'Instagram', color: 'hover:text-pink-400' },
    { icon: Youtube, name: 'YouTube', color: 'hover:text-red-400' },
  ];

  const bgClass = isDark 
    ? 'bg-gradient-to-br from-pink-900/30 via-rose-900/30 to-red-900/30 border-pink-500/30 shadow-pink-500/10' 
    : 'bg-gradient-to-br from-pink-50 via-rose-50 to-red-50 border-pink-200 shadow-pink-200/20';
  
  const textClass = isDark ? 'text-pink-300' : 'text-pink-700';
  const buttonClass = isDark 
    ? 'bg-pink-950/40 border-pink-500/30 text-pink-300 hover:bg-pink-900/50' 
    : 'bg-white/60 border-pink-200 text-pink-600 hover:bg-pink-100';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-lg shadow-lg p-4`}>
      <h3 className={`text-sm font-semibold ${textClass} mb-3 flex items-center`}>
        <Share2 className="w-4 h-4 mr-2" />
        Social Connect
      </h3>
      <div className="grid grid-cols-2 gap-2">
        {socialLinks.map(({ icon: Icon, name, color }) => (
          <button
            key={name}
            className={`p-2 rounded-lg border transition-all duration-300 ${buttonClass} ${color} flex flex-col items-center`}
            title={`Share on ${name}`}
          >
            <Icon className="w-4 h-4" />
            <span className="text-xs mt-1">{name}</span>
          </button>
        ))}
      </div>
    </div>
  );
};

// Media Controls Component
const MediaControls = ({ isPlaying, setIsPlaying, isDark }) => {
  const bgClass = isDark 
    ? 'bg-gradient-to-br from-emerald-900/30 via-teal-900/30 to-cyan-900/30 border-emerald-500/30 shadow-emerald-500/10' 
    : 'bg-gradient-to-br from-emerald-50 via-teal-50 to-cyan-50 border-emerald-200 shadow-emerald-200/20';
  
  const textClass = isDark ? 'text-emerald-300' : 'text-emerald-700';
  const buttonClass = isDark 
    ? 'bg-emerald-950/40 border-emerald-500/30 text-emerald-400 hover:bg-emerald-900/50' 
    : 'bg-white/60 border-emerald-200 text-emerald-600 hover:bg-emerald-100';
  
  const activeClass = isDark 
    ? 'bg-emerald-600/40 border-emerald-400/40 text-emerald-200' 
    : 'bg-emerald-200 border-emerald-400 text-emerald-800';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-lg shadow-lg p-4`}>
      <h3 className={`text-sm font-semibold ${textClass} mb-3 flex items-center`}>
        <Video className="w-4 h-4 mr-2" />
        Media Hub
      </h3>
      <div className="grid grid-cols-2 gap-2">
        <button
          onClick={() => setIsPlaying(!isPlaying)}
          className={`p-2 rounded-lg border transition-all duration-300 flex flex-col items-center ${
            isPlaying ? activeClass : buttonClass
          }`}
        >
          {isPlaying ? <Pause className="w-4 h-4" /> : <Play className="w-4 h-4" />}
          <span className="text-xs mt-1">{isPlaying ? 'Pause' : 'Play'}</span>
        </button>
        <button className={`p-2 rounded-lg border transition-all duration-300 flex flex-col items-center ${buttonClass}`}>
          <Video className="w-4 h-4" />
          <span className="text-xs mt-1">Video</span>
        </button>
        <button className={`p-2 rounded-lg border transition-all duration-300 flex flex-col items-center ${buttonClass}`}>
          <Volume2 className="w-4 h-4" />
          <span className="text-xs mt-1">Audio</span>
        </button>
        <button className={`p-2 rounded-lg border transition-all duration-300 flex flex-col items-center ${buttonClass}`}>
          <Download className="w-4 h-4" />
          <span className="text-xs mt-1">Download</span>
        </button>
      </div>
    </div>
  );
};

// Progress Tracker Component
const ProgressTracker = ({ day, isDark }) => {
  const bgClass = isDark 
    ? 'bg-gradient-to-br from-violet-900/30 via-purple-900/30 to-fuchsia-900/30 border-violet-500/30 shadow-violet-500/10' 
    : 'bg-gradient-to-br from-violet-50 via-purple-50 to-fuchsia-50 border-violet-200 shadow-violet-200/20';
  
  const textClass = isDark ? 'text-violet-300' : 'text-violet-700';
  const secondaryTextClass = isDark ? 'text-violet-400' : 'text-violet-600';
  const progressBg = isDark ? 'bg-violet-950/40 border-violet-500/30' : 'bg-gray-200 border-violet-200';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-lg shadow-lg p-4`}>
      <h3 className={`text-sm font-semibold ${textClass} mb-3 flex items-center`}>
        <Calendar className="w-4 h-4 mr-2" />
        Progress Track
      </h3>
      <div className="space-y-3">
        <div className="flex justify-between items-center">
          <span className={`text-xs ${secondaryTextClass}`}>Days Completed</span>
          <span className={`text-xs ${textClass} font-semibold`}>{Math.max(0, day - 1)}/30</span>
        </div>
        <div className={`w-full ${progressBg} rounded-full h-2 border`}>
          <div 
            className="bg-gradient-to-r from-violet-500 to-purple-500 h-2 rounded-full transition-all duration-500" 
            style={{width: `${Math.min(100, ((Math.max(0, day - 1)) / 30) * 100)}%`}}
          ></div>
        </div>
        <p className={`text-xs ${secondaryTextClass} text-center`}>Keep building your spiritual journey!</p>
      </div>
    </div>
  );
};

// Daily Reminder Component
const DailyReminder = ({ isDark }) => {
  const bgClass = isDark 
    ? 'bg-gradient-to-br from-indigo-900/30 via-blue-900/30 to-sky-900/30 border-indigo-500/30 shadow-indigo-500/10' 
    : 'bg-gradient-to-br from-indigo-50 via-blue-50 to-sky-50 border-indigo-200 shadow-indigo-200/20';
  
  const textClass = isDark ? 'text-indigo-300' : 'text-indigo-700';
  const secondaryTextClass = isDark ? 'text-indigo-400' : 'text-indigo-600';
  const buttonClass = isDark 
    ? 'bg-indigo-950/40 border-indigo-500/30 text-indigo-400 hover:bg-indigo-900/50' 
    : 'bg-white/60 border-indigo-200 text-indigo-600 hover:bg-indigo-100';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-lg shadow-lg p-4`}>
      <h3 className={`text-sm font-semibold ${textClass} mb-3 flex items-center`}>
        <Bell className="w-4 h-4 mr-2" />
        Daily Reminder
      </h3>
      <div className="space-y-3">
        <div className="text-center">
          <p className={`text-xs ${secondaryTextClass}`}>Next session in:</p>
          <p className={`text-lg ${textClass} font-bold`}>23h 45m</p>
        </div>
        <button className={`w-full px-3 py-2 border rounded-lg transition-all duration-300 text-xs ${buttonClass}`}>
          Set Reminder
        </button>
      </div>
    </div>
  );
};

// Devotional Selector Component
const DevotionalSelector = ({ setDevotional, currentDevotional, isDark, showMore, toggleShowMore }) => {
  const devotionals = [
    { 
      id: "family", 
      label: "Overcoming Family Patterns", 
      icon: BookOpen, 
      gradient: "from-slate-600 to-slate-800",
      darkGlow: "border-slate-500/30 shadow-slate-500/10 from-slate-900/30 to-slate-800/30",
      lightGlow: "border-slate-300 shadow-slate-200/20 from-slate-100 to-slate-200",
      textColor: isDark ? "text-slate-300" : "text-slate-700",
      description: "Breaking generational cycles"
    },
    { 
      id: "hope", 
      label: "It Is Not Over: God Will Fix It", 
      icon: Sun, 
      gradient: "from-amber-600 to-orange-700",
      darkGlow: "border-amber-500/30 shadow-amber-500/10 from-amber-900/30 to-orange-900/30",
      lightGlow: "border-amber-300 shadow-amber-200/20 from-amber-100 to-orange-100",
      textColor: isDark ? "text-amber-300" : "text-amber-700",
      description: "Finding hope and restoration"
    },
    { 
      id: "decree", 
      label: "Revoking Every Evil Decree", 
      icon: Heart, 
      gradient: "from-red-600 to-rose-700",
      darkGlow: "border-red-500/30 shadow-red-500/10 from-red-900/30 to-rose-900/30",
      lightGlow: "border-red-300 shadow-red-200/20 from-red-100 to-rose-100",
      textColor: isDark ? "text-red-300" : "text-red-700",
      description: "Breaking spiritual strongholds"
    },
    { 
      id: "hearing", 
      label: "Hearing God", 
      icon: Volume2, 
      gradient: "from-blue-600 to-indigo-700",
      darkGlow: "border-blue-500/30 shadow-blue-500/10 from-blue-900/30 to-indigo-900/30",
      lightGlow: "border-blue-300 shadow-blue-200/20 from-blue-100 to-indigo-100",
      textColor: isDark ? "text-blue-300" : "text-blue-700",
      description: "Developing spiritual discernment"
    },
    { 
      id: "seeing", 
      label: "Seeing Clearly", 
      icon: Eye, 
      gradient: "from-emerald-600 to-teal-700",
      darkGlow: "border-emerald-500/30 shadow-emerald-500/10 from-emerald-900/30 to-teal-900/30",
      lightGlow: "border-emerald-300 shadow-emerald-200/20 from-emerald-100 to-teal-100",
      textColor: isDark ? "text-emerald-300" : "text-emerald-700",
      description: "Gaining spiritual insight"
    },
  ];

  const displayedDevotionals = showMore ? devotionals : devotionals.slice(0, 4);

  const bgClass = isDark 
    ? 'bg-gradient-to-br from-purple-900/30 via-indigo-900/30 to-blue-900/30 border-purple-500/30 shadow-purple-500/10' 
    : 'bg-gradient-to-br from-purple-50 via-indigo-50 to-blue-50 border-purple-200 shadow-purple-200/20';
  
  const textClass = isDark ? 'text-purple-300' : 'text-purple-700';
  const buttonClass = isDark 
    ? 'bg-purple-950/40 border-purple-500/30 text-purple-400 hover:bg-purple-900/50' 
    : 'bg-white/60 border-purple-200 text-purple-600 hover:bg-purple-100';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-xl shadow-lg p-5`}>
      <div className="flex items-center justify-between mb-4">
        <h2 className={`text-lg font-semibold ${textClass} flex items-center`}>
          <Menu className="w-5 h-5 mr-2" />
          Devotional Programs
        </h2>
        <div className="flex items-center space-x-2">
          <button className={`p-2 rounded-lg border transition-all duration-300 ${buttonClass}`}>
            <Eye className="w-4 h-4" />
          </button>
          <button className={`p-2 rounded-lg border transition-all duration-300 ${buttonClass}`}>
            <Download className="w-4 h-4" />
          </button>
        </div>
      </div>
      <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3">
        {displayedDevotionals.map(({ id, label, icon: Icon, gradient, darkGlow, lightGlow, textColor, description }) => {
          const glowClass = isDark ? darkGlow : lightGlow;
          const isSelected = currentDevotional === id;
          
          return (
            <button
              key={id}
              onClick={() => setDevotional(id)}
              className={`p-3 rounded-lg border backdrop-blur-md text-left transition-all duration-300 ${
                isSelected 
                  ? `border-white/50 ${isDark ? 'bg-white/10' : 'bg-gray-100'} transform scale-105 shadow-lg ${glowClass.split(' ')[1]}` 
                  : `${glowClass} ${isDark ? 'hover:bg-gray-800/50' : 'hover:bg-white/70'} hover:scale-102`
              }`}
            >
              <div className={`w-8 h-8 rounded-lg bg-gradient-to-br ${gradient} flex items-center justify-center mb-3 shadow-lg`}>
                <Icon className="w-4 h-4 text-white" />
              </div>
              <h3 className={`text-sm font-semibold ${textColor} mb-1 leading-tight`}>{label}</h3>
              <p className={`text-xs ${isDark ? 'text-gray-400' : 'text-gray-600'} leading-relaxed`}>{description}</p>
            </button>
          );
        })}
        
        {/* More Button */}
        {!showMore && devotionals.length > 4 && (
          <button
            onClick={toggleShowMore}
            className={`p-3 rounded-lg border backdrop-blur-md text-center transition-all duration-300 ${buttonClass} flex flex-col items-center justify-center`}
          >
            <Menu className="w-6 h-6 mb-2" />
            <span className="text-sm font-semibold">MORE</span>
          </button>
        )}
      </div>
      
      {showMore && (
        <div className="mt-4 text-center">
          <button
            onClick={toggleShowMore}
            className={`px-4 py-2 rounded-lg border transition-all duration-300 ${buttonClass} text-sm`}
          >
            Show Less
          </button>
        </div>
      )}
    </div>
  );
};

// Day Navigator Component
const DayNavigator = ({ day, setDay, startEditing, devotionalLabel, isDark }) => {
  const bgClass = isDark 
    ? 'bg-gradient-to-r from-yellow-900/30 via-orange-900/30 to-amber-900/30 border-yellow-500/30 shadow-yellow-500/10' 
    : 'bg-gradient-to-r from-yellow-50 via-orange-50 to-amber-50 border-yellow-200 shadow-yellow-200/20';
  
  const textClass = isDark ? 'text-yellow-300' : 'text-yellow-700';
  const secondaryTextClass = isDark ? 'text-yellow-400/80' : 'text-yellow-600';
  const buttonClass = isDark 
    ? 'bg-yellow-950/40 border-yellow-500/30 text-yellow-400 hover:bg-yellow-900/50' 
    : 'bg-white/60 border-yellow-200 text-yellow-600 hover:bg-yellow-100';
  const activeButtonClass = isDark 
    ? 'bg-yellow-600/40 border-yellow-400/40 text-yellow-200 hover:bg-yellow-600/50' 
    : 'bg-yellow-200 border-yellow-400 text-yellow-800 hover:bg-yellow-300';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-xl shadow-lg p-4`}>
      <div className="flex items-center justify-between">
        <div className="flex items-center space-x-3">
          <button
            onClick={() => setDay((prev) => Math.max(1, prev - 1))}
            disabled={day <= 1}
            className={`px-3 py-2 rounded-lg border transition-all duration-300 flex items-center disabled:opacity-50 disabled:cursor-not-allowed ${buttonClass}`}
          >
            <ChevronLeft className="w-4 h-4" />
            <span className="ml-1 hidden sm:inline text-xs">Prev</span>
          </button>

          <div className="text-center">
            <h2 className={`text-lg font-bold ${textClass} flex items-center`}>
              <Calendar className="w-4 h-4 mr-2" />
              Day {day}
            </h2>
            <p className={`text-xs ${secondaryTextClass} mt-1 truncate max-w-[150px]`}>{devotionalLabel}</p>
          </div>
        </div>

        <div className="flex gap-2">
          <button className={`px-2 py-2 rounded-lg border transition-all duration-300 flex items-center ${buttonClass}`}>
            <Eye className="w-4 h-4" />
            <span className="ml-1 hidden sm:inline text-xs">View</span>
          </button>
          <button className={`px-2 py-2 rounded-lg border transition-all duration-300 flex items-center ${buttonClass}`}>
            <Download className="w-4 h-4" />
          </button>
          <button
            onClick={startEditing}
            className={`px-3 py-2 rounded-lg border transition-all duration-300 flex items-center ${activeButtonClass}`}
          >
            <Edit className="w-4 h-4" />
            <span className="ml-1 hidden sm:inline text-xs">Edit</span>
          </button>
          <button
            onClick={() => setDay((prev) => prev + 1)}
            className={`px-3 py-2 rounded-lg border transition-all duration-300 flex items-center ${buttonClass}`}
          >
            <span className="mr-1 hidden sm:inline text-xs">Next</span>
            <ChevronRight className="w-4 h-4" />
          </button>
        </div>
      </div>
    </div>
  );
};

// Devotional Content Component
const DevotionalContent = ({ currentContent, handleInputChange, saveProgress, hasContent, isDark }) => {
  const bgClass = isDark 
    ? 'bg-gradient-to-br from-teal-900/30 via-cyan-900/30 to-blue-900/30 border-teal-500/30 shadow-teal-500/10' 
    : 'bg-gradient-to-br from-teal-50 via-cyan-50 to-blue-50 border-teal-200 shadow-teal-200/20';
  
  const textClass = isDark ? 'text-teal-300' : 'text-teal-700';
  const secondaryTextClass = isDark ? 'text-teal-400/80' : 'text-teal-600';
  const buttonClass = isDark 
    ? 'bg-teal-950/40 border-teal-500/30 text-teal-400 hover:bg-teal-900/50' 
    : 'bg-white/60 border-teal-200 text-teal-600 hover:bg-teal-100';
  
  const activeButtonClass = isDark 
    ? 'bg-teal-600/40 border-teal-400/40 text-teal-200 hover:bg-teal-600/50' 
    : 'bg-teal-200 border-teal-400 text-teal-800 hover:bg-teal-300';
  
  const textareaClass = isDark 
    ? 'bg-teal-950/40 border-teal-500/30 text-teal-100 placeholder-teal-400/60 focus:border-teal-400/50 focus:ring-teal-500/30' 
    : 'bg-white/80 border-teal-200 text-teal-800 placeholder-teal-500/60 focus:border-teal-400 focus:ring-teal-300/30';

  return (
    <div className={`${bgClass} backdrop-blur-md border rounded-xl shadow-lg`}>
      <div className={`p-4 border-b ${isDark ? 'border-teal-500/30' : 'border-teal-200'} flex items-center justify-between`}>
        <div>
          <h3 className={`text-lg font-semibold ${textClass} mb-1`}>Daily Reflection</h3>
          <p className={`text-xs ${secondaryTextClass}`}>Record your thoughts and insights</p>
        </div>
        <div className="flex items-center space-x-2">
          <button className={`p-2 rounded-lg border transition-all duration-300 ${buttonClass}`}>
            <Share2 className="w-4 h-4" />
          </button>
          <button className={`p-2 rounded-lg border transition-all duration-300 ${buttonClass}`}>
            <Download className="w-4 h-4" />
          </button>
        </div>
      </div>
      <div className="p-4">
        <textarea
          placeholder="Enter your devotional reflection, key insights, prayers, or action points..."
          value={currentContent?.text || ""}
          onChange={(e) => handleInputChange("text", e.target.value)}
          className={`w-full p-3 rounded-lg border resize-none focus:outline-none focus:ring-2 transition-all duration-300 ${textareaClass}`}
          rows={6}
        />
        <div className="flex justify-between items-center mt-4">
          <div className={`text-xs ${secondaryTextClass} flex items-center space-x-4`}>
            <span>{currentContent?.text ? `${currentContent.text.length} chars` : 'No content yet'}</span>
            <span>Auto-saved</span>
          </div>
          <div className="flex items-center space-x-2">
            <button className={`px-3 py-2 border rounded-lg transition-all duration-300 font-medium flex items-center ${buttonClass}`}>
              <Eye className="w-4 h-4 mr-1" />
              <span className="text-xs">Preview</span>
            </button>
            <button
              onClick={saveProgress}
              className={`px-4 py-2 border rounded-lg transition-all duration-300 font-medium flex items-center ${activeButtonClass}`}
            >
              <Save className="w-4 h-4 mr-1" />
              <span className="text-xs">Save</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  );
};

// Edit Modal Component
const EditModal = ({
  editMode,
  setEditMode,
  editingContent,
  handleEditContentChange,
  saveEditedContent,
  isDark
}) => {
  if (!editMode) return null;

  const bgClass = isDark 
    ? 'bg-gradient-to-br from-gray-800 to-gray-900 border-gray-600/50' 
    : 'bg-gradient-to-br from-white to-gray-50 border-gray-300';
  
  const headerBgClass = isDark 
    ? 'bg-gradient-to-r from-blue-900/30 to-purple-900/30 border-gray-600/50' 
    : 'bg-gradient-to-r from-blue-100 to-purple-100 border-gray-300';
  
  const textClass = isDark ? 'text-white' : 'text-gray-800';
  const textareaClass = isDark 
    ? 'bg-gray-900/80 text-white placeholder-gray-400 border-gray-600/50 focus:border-blue-500/50' 
    : 'bg-white text-gray-800 placeholder-gray-500 border-gray-300 focus:border-blue-500';
  
  const footerBgClass = isDark ? 'bg-gray-800/50 border-gray-600/50' : 'bg-gray-50 border-gray-300';

  return (
    <div className="fixed inset-0 bg-black/80 backdrop-blur-sm flex items-center justify-center z-50 p-4">
      <div className={`${bgClass} border rounded-xl max-w-4xl w-full max-h-[90vh] overflow-hidden shadow-2xl`}>
        <div className={`p-6 border-b ${headerBgClass} flex items-center justify-between`}>
          <h2 className={`text-xl font-bold ${textClass} flex items-center`}>
            <Edit className="w-5 h-5 mr-2" />
            Edit Devotional Content
          </h2>
          <div className="flex items-center space-x-2">
            <button className={`p-2 rounded-lg ${isDark ? 'bg-gray-700/50 hover:bg-gray-600/50 text-gray-300' : 'bg-gray-200 hover:bg-gray-300 text-gray-600'} transition-all`}>
              <Share2 className="w-4 h-4" />
            </button>
            <button className={`p-2 rounded-lg ${isDark ? 'bg-gray-700/50 hover:bg-gray-600/50 text-gray-300' : 'bg-gray-200 hover:bg-gray-300 text-gray-600'} transition-all`}>
              <Download className="w-4 h-4" />
            </button>
            <button onClick={() => setEditMode(false)} className={`p-2 rounded-lg ${isDark ? 'bg-red-600/50 hover:bg-red-600/70 text-red-200' : 'bg-red-200 hover:bg-red-300 text-red-600'} transition-all`}>
              <X className="w-4 h-4" />
            </button>
          </div>
        </div>
        <div className="p-6">
          <textarea
            value={editingContent?.text || ""}
            onChange={(e) => handleEditContentChange("text", e.target.value)}
            className={`w-full p-4 rounded-lg resize-none border focus:outline-none transition-colors ${textareaClass}`}
            rows={15}
            placeholder="Enter your devotional reflection..."
          />
        </div>
        <div className={`p-6 border-t ${footerBgClass} flex gap-3 justify-end`}>
          <button
            onClick={() => setEditMode(false)}
            className={`px-6 py-2 rounded-lg transition-all ${isDark ? 'bg-gray-600/50 hover:bg-gray-600/70 text-white' : 'bg-gray-300 hover:bg-gray-400 text-gray-700'}`}
          >
            Cancel
          </button>
          <button className={`px-6 py-2 rounded-lg transition-all flex items-center ${isDark ? 'bg-blue-600/50 hover:bg-blue-600/70 text-white' : 'bg-blue-500 hover:bg-blue-600 text-white'}`}>
            <Eye className="w-4 h-4 mr-2" />
            Preview
          </button>
          <button
            onClick={saveEditedContent}
            className={`px-6 py-2 rounded-lg transition-all flex items-center ${isDark ? 'bg-green-600/50 hover:bg-green-600/70 text-white' : 'bg-green-500 hover:bg-green-600 text-white'}`}
          >
            <Save className="w-4 h-4 mr-2" />
            Save Changes
          </button>
        </div>
      </div>
    </div>
  );
};

// Footer Component
const ConnectFooter = ({ isDark }) => {
  const textClass = isDark ? 'text-gray-400' : 'text-gray-600';
  const borderClass = isDark ? 'border-gray-700/50' : 'border-gray-300/50';

  return (
    <footer className={`text-center mt-12 pt-6 border-t ${borderClass}`}>
      <div className={`${textClass} mb-2`}>
        <p className="text-sm">© 2025 Soumet Connect. Designed by Oghale Elebe JP.</p>
      </div>
    </footer>
  );
};

// Main App Component
export default function SoumetConnect() {
  const [devotional, setDevotional] = useState(null);
  const [day, setDay] = useState(1);
  const [contents, setContents] = useState({});
  const [editMode, setEditMode] = useState(false);
  const [editingContent, setEditingContent] = useState(null);
  const [toast, setToast] = useState(null);
  const [menuOpen, setMenuOpen] = useState(false);
  const [isPlaying, setIsPlaying] = useState(false);
  const [isDark, setIsDark] = useState(true);
  const [showMore, setShowMore] = useState(false);

  const devotionalLabels = {
    family: "Overcoming Family Patterns",
    hope: "It Is Not Over: God Will Fix It",
    decree: "Revoking Every Evil Decree",
    hearing: "Hearing God",
    seeing: "Seeing Clearly"
  };

  const currentKey = `${devotional}-${day}`;
  const currentContent = contents[currentKey];

  const showToast = (message, type = 'success') => {
    setToast({ message, type });
    setTimeout(() => setToast(null), 3000);
  };

  const handleInputChange = (field, value) => {
    setContents((prev) => ({
      ...prev,
      [currentKey]: { ...prev[currentKey], [field]: value },
    }));
  };

  const saveProgress = () => {
    showToast("Progress saved successfully", "success");
  };

  const startEditing = () => {
    setEditingContent(currentContent || {});
    setEditMode(true);
  };

  const handleEditContentChange = (field, value) => {
    setEditingContent((prev) => ({ ...prev, [field]: value }));
  };

  const saveEditedContent = () => {
    setContents((prev) => ({
      ...prev,
      [currentKey]: editingContent,
    }));
    setEditMode(false);
    showToast("Content updated successfully", "success");
  };

  const toggleMenu = () => {
    setMenuOpen(!menuOpen);
  };

  const toggleTheme = () => {
    setIsDark(!isDark);
  };

  const toggleShowMore = () => {
    setShowMore(!showMore);
  };

  const mainBgClass = isDark ? 'bg-black' : 'bg-gray-50';
  const textClass = isDark ? 'text-white' : 'text-gray-800';

  return (
    <div className={`min-h-screen ${mainBgClass} ${textClass} flex relative overflow-hidden`}>
      {/* Animated Background Effects */}
      {isDark && (
        <div className="absolute inset-0 overflow-hidden pointer-events-none">
          {/* Primary Glow Effects */}
          <div className="absolute top-1/4 left-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl animate-pulse"></div>
          <div className="absolute top-3/4 right-1/4 w-80 h-80 bg-blue-500/8 rounded-full blur-3xl animate-pulse delay-1000"></div>
          <div className="absolute bottom-1/4 left-1/3 w-72 h-72 bg-cyan-500/6 rounded-full blur-3xl animate-pulse delay-2000"></div>
          
          {/* Secondary Accent Glows */}
          <div className="absolute top-1/2 right-1/3 w-64 h-64 bg-pink-500/8 rounded-full blur-2xl animate-pulse delay-3000"></div>
          <div className="absolute bottom-1/3 right-1/2 w-56 h-56 bg-emerald-500/6 rounded-full blur-2xl animate-pulse delay-4000"></div>
          
          {/* Subtle Moving Particles */}
          <div className="absolute top-1/6 left-1/2 w-4 h-4 bg-white/20 rounded-full blur-sm animate-bounce delay-500"></div>
          <div className="absolute top-2/3 left-1/5 w-3 h-3 bg-blue-300/30 rounded-full blur-sm animate-bounce delay-1500"></div>
          <div className="absolute bottom-1/5 right-1/6 w-2 h-2 bg-purple-300/40 rounded-full blur-sm animate-bounce delay-2500"></div>
        </div>
      )}

      {/* Navigation Sidebar */}
      <NavigationMenu isOpen={menuOpen} toggleMenu={toggleMenu} isDark={isDark} />
      
      {/* Main Content */}
      <div className="flex-1 lg:ml-0 relative z-10">
        <div className="max-w-7xl mx-auto px-4 py-4">
          <Header isDark={isDark} toggleTheme={toggleTheme} />

          {/* Newspaper Column Layout */}
          <div className="grid lg:grid-cols-6 gap-4 mb-6">
            {/* Main Content - 4 columns */}
            <div className="lg:col-span-4 space-y-4">
              <DevotionalSelector 
                setDevotional={setDevotional} 
                currentDevotional={devotional} 
                isDark={isDark}
                showMore={showMore}
                toggleShowMore={toggleShowMore}
              />

              {devotional && (
                <>
                  <DayNavigator 
                    day={day} 
                    setDay={setDay} 
                    startEditing={startEditing}
                    devotionalLabel={devotionalLabels[devotional]}
                    isDark={isDark}
                  />
                  <DevotionalContent
                    currentContent={currentContent}
                    handleInputChange={handleInputChange}
                    saveProgress={saveProgress}
                    hasContent={!!currentContent?.text}
                    isDark={isDark}
                  />
                </>
              )}
            </div>

            {/* Right Sidebar - 2 columns */}
            <div className="lg:col-span-2 space-y-4">
              <SocialMedia isDark={isDark} />
              <MediaControls isPlaying={isPlaying} setIsPlaying={setIsPlaying} isDark={isDark} />
              <ProgressTracker day={day} isDark={isDark} />
              <DailyReminder isDark={isDark} />
            </div>
          </div>

          <EditModal
            editMode={editMode}
            setEditMode={setEditMode}
            editingContent={editingContent}
            handleEditContentChange={handleEditContentChange}
            saveEditedContent={saveEditedContent}
            isDark={isDark}
          />

          <ConnectFooter isDark={isDark} />

          {/* Professional Toast Notification */}
          {toast && (
            <div className={`fixed bottom-6 right-6 px-6 py-4 rounded-lg shadow-lg z-50 border ${
              toast.type === 'success' 
                ? 'bg-green-600 border-green-500 text-white' 
                : 'bg-red-600 border-red-500 text-white'
            }`}>
              <div className="flex items-center">
                <Save className="w-4 h-4 mr-2" />
                {toast.message}
              </div>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}