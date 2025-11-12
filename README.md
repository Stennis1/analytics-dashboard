# EventFlow Analytics Dashboard

A modern, responsive web application for event organizers to track sessions, analyze attendance, and visualize event performance metrics in real-time.

![EventFlow Dashboard](https://img.shields.io/badge/Status-In%20Development-blue)
![React](https://img.shields.io/badge/React-18.2+-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178C6?logo=typescript)
![Azure](https://img.shields.io/badge/Yet%20to%20Deploy%20on-Azure-0078D4?logo=microsoftazure)

## 🚀 Features

### Core Functionality
- **📊 Real-time Analytics Dashboard** - Get instant insights with key event metrics and visualizations
- **👥 Session & Attendee Tracking** - Detailed view of all sessions with attendance numbers and speaker information
- **📈 Interactive Data Visualizations** - Charts and graphs for attendance trends and session popularity
- **🔍 Dynamic Filtering** - Filter sessions by date, speaker, or custom criteria
- **♿ Full Accessibility** - WCAG 2.1 compliant with keyboard navigation and screen reader support

### Technical Highlights
- **⚡ Performance Optimized** - Memoized components and efficient re-rendering
- **📱 Responsive Design** - Seamless experience across desktop, tablet, and mobile
- **🎯 Type-Safe** - Built with TypeScript for better developer experience
- **🌙 Accessible** - High contrast ratios, ARIA labels, and keyboard navigation

## 🏗️ Architecture

### Component Structure
```
App
├── Header
├── ErrorBoundary
│   ├── Dashboard (Conditional View)
│   │   ├── MetricsDisplay
│   │   └── AttendanceChart
│   └── SessionList (Conditional View)
│       ├── FilterControls
│       └── SessionItem
```

### Data Flow
- **Centralized State Management** in root `App` component
- **Unidirectional Data Flow** - Props down, events up
- **Predictable State Updates** using React hooks

## 🛠️ Technology Stack

- **Frontend Framework:** React 18.2+ with TypeScript
- **Build Tool:** Vite
- **Styling:** CSS3 with CSS Grid & Flexbox
- **Charts:** Chart.js with react-chartjs-2
- **Deployment:** Microsoft Azure Static Web Apps
- **Accessibility:** ESLint jsx-a11y, ARIA attributes
- **Performance:** React.memo, useMemo, useCallback

## 📦 Installation

### Prerequisites
- Node.js 18.0 or higher
- npm or yarn

### Local Development (In Building Phase)
```bash
# Clone the repository
git clone https://github.com/your-username/eventflow-analytics.git

# Navigate to project directory
cd eventflow-analytics

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Run tests
npm test
```

## 🎯 Usage

### For Event Organizers
1. **View Dashboard** - Get an overview of key metrics and attendance trends
2. **Browse Sessions** - See detailed session information with filtering options
3. **Analyze Data** - Use interactive charts to understand event performance
4. **Export Reports** - Generate insights for post-event analysis

## 🚀 Deployment (Yet to Deploy)

The application is automatically deployed to **Azure Static Web Apps**:

**Production URL:** https://your-app.azurestaticapps.net

### Deployment Process
1. Push to `main` branch triggers automatic deployment
2. GitHub Actions handles build and deployment
3. Zero-downtime deployments with staging slots

## 📊 Project Phases

### Phase 1: Planning & Design ✅
- [x] Architecture documentation
- [x] Component specifications
- [x] Data flow design

### Phase 2: Core Implementation & Accessibility 🚧
- [ ] Build accessible UI components
- [ ] Implement data visualizations
- [ ] Add filtering functionality
- [ ] Deploy to Azure

### Phase 3: Performance Optimization 📈
- [ ] Implement memoization
- [ ] Optimize re-renders
- [ ] Bundle size optimization

### Phase 4: Portfolio Preparation 🎯
- [ ] Comprehensive documentation
- [ ] Case study
- [ ] Code cleanup and final review

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- Built as part of the Microsoft React Development Course
- Chart components powered by Chart.js
- Icons from Lucide React
- Deployment infrastructure by Microsoft Azure
