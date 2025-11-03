# Project Ideas for the Workshop

The exercises uses a multi-agent development workflow with specialized AI agents for different phases of development.

## Learning Goals

- **Adopt an Agentic Workflow:** The primary goal is to practice building a complete prototype using an AI agent as your primary development partner.
- **Practice Blueprint Creation:** Start new projects by collaborating with an AI Architect to establish foundational technical decisions before implementation.
- **Practice Thread Isolation:** Learn to manage complexity by assigning distinct, single-purpose tasks to separate, isolated agent threads.
- **Utilize AI for Planning:** Use the agent not just for coding, but as a strategic partner to create a project roadmap and a TODO.md to track progress.
- **Task Decomposition:** Break down the larger project goal into small, well-defined tasks that can be completed by a focused agent in a single thread.
- **Practice Memory Persistence Between Agent Threads:** Utilize markdown files (BLUEPRINT.md, research.md, developer_todo.md) in a systematic way to ground agents in a shared 'memory'.
- **Leverage Agent Roles:** Improve the quality of the AI's output by assigning it specific, expert roles for different phases of the project.

### Getting Started

1. **Choose your project**: Choose from the list of options available for project implementation
    - [Project 1: Road Safety Alert Dashboard](#project-1--road-safety-alert-dashboard) - Beginner-friendly weather-focused dashboard
    - [Project 2: Winter Road Safety Dashboard](#project-2---winter-road-safety-dashboard) - Computer vision road monitoring
    - [Project 3: AI-Powered Road Safety Assistant](#project-3---ai-powered-road-safety-assistant-advanced) - Advanced AI reasoning with MCP
2. **Review API Documentation**: Explore the documentation to understand data structures
3. **Choose Your Path**: 
   - Path A (spec-kit workflow) for streamlined development
   - Path B (manual multi-agent workflow) for deeper understanding of agent collaboration

If you're impatient and want to dive in:
1. Read the **Exercise Guide** and follow the steps
2. Reference the **Agents and Prompts** documentation when you need clarification

If you prefer to understand the system first:
1. Read the **Agents and Prompts** documentation to learn about the workflow
2. Then follow the **Exercise Guide** to build the project

**References**

- **[Agents and Prompts](Agents%20and%20Prompts.md)** - Comprehensive system reference detailing the agent architecture, roles, capabilities, and protocols. Read this if you want to understand how the multi-agent system works.

- **[Exercise Guide](exercise-guide.md)** - Step-by-step walkthrough for building the application using either the spec-kit workflow (Path A) or the manual multi-agent workflow (Path B).

## Choosing Your Project

| Aspect | Project 1 | Project 2 | Project 3 |
|--------|-----------|-----------|-----------|
| **Name** | Road Safety Alert Dashboard | Winter Road Safety Dashboard | AI-Powered Road Safety Assistant |
| **Complexity** | Beginner-Intermediate | Intermediate-Advanced | Advanced |
| **API Type** | REST API | REST API | MCP + REST API |
| **Data Focus** | Forecasted weather | Observed conditions | Combined intelligence |
| **AI Integration** | Display only | Display + analysis | AI reasoning + decision making |
| **Best For** | Learning workflow basics | Complex data handling | AI integration |


**Recommendation**: 
- **New to agentic workflows?** Start with **Project 1**
- **Comfortable with APIs?** Try **Project 2** for computer vision integration
- **Want cutting-edge AI?** Choose **Project 3** for MCP and AI reasoning

## Project 1- Road Safety Alert Dashboard

### Objective
Build a web application that helps drivers and transportation professionals make informed decisions about road safety by visualizing real-time and forecasted road weather conditions using the Xweather Road Weather Conditions API.

### Goal
Practice the agentic workflow (either spec-kit or manual multi-agent approach) to develop a complete, functional web application from initial specification through implementation.

### Scenario
**You are a developer tasked with creating a road safety tool for a transportation company.** Winter weather is approaching, and the operations team needs a way to quickly assess road conditions for their routes. They need to see at a glance whether roads are safe (GREEN), require caution (YELLOW), or are potentially hazardous (RED). The tool should display road surface conditions (dry, wet, ice, snow) and surface temperatures to help them make informed decisions about travel timing and route selection.

### Required Features

Implement the following core features:

#### 1. Location Search & Data Retrieval
- Accept location input (city name, postal code, or coordinates)
- Fetch road condition data from Xweather API
- Display current road surface condition (DRY, MOIST, WET, SLUSH, SNOW, ICE)
- Show road surface temperature
- Handle errors and invalid locations gracefully

#### 2. Safety Status Visualization
- Calculate and display current road safety status (GREEN/YELLOW/RED)
- Apply color-coded indicators based on conditions
- Show clear visual representation of hazard levels
- Display location information and timestamp

#### 3. 24-Hour Forecast Timeline
- Present forecast for the next 24 hours
- Visualize temperature trends over time
- Show condition changes throughout the day
- Highlight potentially dangerous time periods

### API Information

- **Endpoint**: `https://data.api.xweather.com/roadweather/conditions/{action}`
- **Actions**: `:id` (single location), `route` (multi-point routes)
- **Authentication**: Requires `client_id` and `client_secret` parameters
- **Documentation**: [Xweather Road Weather API](https://www.xweather.com/docs/weather-api/endpoints/roadweather-conditions)

**Note:** The API has a 5x cost multiplier per request. Consider implementing request throttling and caching strategies.

---

## Project 2 - Winter Road Safety Dashboard

### Objective
Build a real-time winter road safety monitoring dashboard that helps winter maintenance teams visualize road conditions from mobile observations using the Vaisala RoadAI API. The application will display MD30 road weather measurements and RoadAI road weather classifications to support winter maintenance decision-making.

### Goal
Practice the agentic workflow (either spec-kit or manual multi-agent approach) to develop a complete, functional web application from initial specification through implementation. Learn to decompose a complex project into manageable epics and tasks while maintaining consistency through shared documentation artifacts.

### Scenario
**You are a developer tasked with creating a winter road monitoring tool for a city's winter maintenance department.** Winter weather is approaching, and the operations team uses MD30-equipped vehicles to monitor road conditions throughout the city. They need a dashboard to visualize this data in real-time, showing road surface conditions (dry, wet, ice, snow), surface temperatures, and winter-specific hazards. The tool should help them prioritize routes for treatment (salting, plowing) and identify dangerous conditions before they cause accidents.

The maintenance team has access to the Vaisala RoadAI system, which uses MD30 sensors and computer vision to analyze winter road conditions from vehicle-mounted equipment. Your dashboard needs to make this data accessible and actionable for winter maintenance operations.

### Required Features

Implement the following core features:

#### 1. Mobile Observations Display
- Fetch and display mobile observations from the RoadAI API
- Show observation metadata (timestamp, user, track length)
- Filter observations by date range
- Display location data on a map or as coordinates
- Handle pagination for large datasets (30 records per page)

#### 2. Winter Road Condition Visualization
- Display MD30 road weather measurements
- Show key winter parameters:
  - Surface state (dry, wet, slush, snow, ice)
  - Surface temperature
  - Ice/snow layer thickness (when present)
  - Road surface friction estimates
  - Dew point temperature
- Use color-coded indicators for different winter conditions
- Display RoadAI road weather classification results
- Show AI confidence scores for winter condition detections

#### 3. Winter Maintenance Decision Support
- Display winter-specific hazard indicators (ice formation risk, snow accumulation)
- Show recommended maintenance actions based on conditions
- Visualize treatment priority areas (routes needing immediate salting/plowing)
- Present time-series data showing condition changes over winter operations
- Highlight critical thresholds (freezing temps, ice detection, heavy snow)

### API Information

- **Base URL**: `https://api.vionice.io/api/v1`
- **Authentication**: API key (query parameter `apikey`) OR username/password to obtain auth token
- **Key Endpoints**:
  - `/mobileObservations` - Road condition data from MD30-equipped vehicles
  - `/shares` - Access available data shares
  - `/parameters` - List of observation parameter types (focus on winter weather parameters)
- **Documentation**: [Vaisala RoadAI API Swagger](https://swagger.vionice.io/)

**Important Notes:**
- The API uses pagination (default 30 records, max 100 per request)
- Location data is returned as GeoJSON (Point, LineString, etc.)
- MD30 measurements include surface state, temperature, and friction estimates
- RoadAI road weather classifications have confidence scores
- Winter maintenance operations typically don't record high-resolution video
- Focus on MD30 sensor data and road weather parameters for winter conditions
- Consider implementing request caching to minimize API calls

---

## Project 3 - AI-Powered Road Safety Assistant (Advanced)

### Objective
Build an intelligent conversational assistant that combines Xweather's Model Context Protocol (MCP) integration with Vaisala RoadAI's real-time observation data to provide comprehensive road safety intelligence. This project leverages AI models' ability to reason with live weather data alongside actual road conditions from camera-equipped vehicles.

### Goal
Practice the agentic workflow while integrating cutting-edge AI capabilities through MCP. Learn to combine multiple data sources (forecasted weather + observed conditions) and enable natural language interaction for complex decision-making scenarios.

### Scenario
**You are developing an AI-powered road safety assistant for a regional transportation authority.** The system needs to answer complex questions that require both predictive weather intelligence and actual road observations. For example: "Should we pre-treat Highway 101 tonight?" requires knowing the forecast (Xweather MCP) and current road infrastructure condition (RoadAI API). The assistant should reason across both data sources to provide actionable recommendations.

### What Makes This Project Advanced

This project combines:
- **Model Context Protocol (MCP)**: Enable AI models to directly access Xweather data through natural conversation
- **Traditional API Integration**: Fetch real-time road observations from Vaisala RoadAI
- **AI Reasoning**: Let AI models correlate weather forecasts with actual road conditions
- **Multi-Source Intelligence**: Combine predictive and observational data for better decisions

**Key Innovation**: Instead of just displaying data, the AI actively reasons about it:
- "Bridge ahead is frozen, adjust speed" (correlating temperature forecast + observed ice)
- "Route has severe potholes + freezing rain tonight = high priority for repair before storm"
- "Solar panels on Highway 5 will have optimal output 10am-2pm tomorrow despite morning clouds"

### Required Features

#### 1. MCP-Powered Weather Intelligence
- Integrate Xweather MCP server into your application
- Enable natural language queries to AI models (ChatGPT or Claude)
- Support queries like:
  - "What's the road weather forecast for [location] this weekend?"
  - "Was there lightning at [location] on [date]?"
  - "Safest route from [city A] to [city B] avoiding weather hazards?"
- Display AI responses in user-friendly format
- Show what weather data the AI accessed

#### 2. Real-Time Observation Integration
- Fetch current road observations from RoadAI API
- Display alongside weather forecasts from MCP
- Show correlations between forecast and observations:
  - Freezing temps predicted + ice patches detected
  - Rain forecast + existing potholes shown
  - Wind advisory + damaged infrastructure flagged
- Use color-coding to highlight critical combinations

#### 3. Conversational Decision Support
- Build chat-based UI for natural language interaction
- Enable complex questions combining both data sources:
  - "Should we deploy salt trucks on [route] tonight?"
  - "Which routes need urgent repair before the storm?"
  - "Is it safe to transport high-profile vehicles through [area] tomorrow?"
- Display AI's reasoning process (how it reached the decision)
- Provide confidence indicators based on data quality
- Include source citations (MCP weather data vs. RoadAI observations)

### Technical Architecture

#### Required Integrations
1. **Xweather MCP Server** 
   - Set up MCP connection to Xweather
   - Configure AI model access (ChatGPT/Claude)
   - Handle natural language queries

2. **Vaisala RoadAI API**
   - Traditional REST API integration
   - Real-time observation fetching
   - GeoJSON data processing
   - **Base URL**: `https://api.vionice.io/api/v1`

3. **AI Orchestration**
   - Combine MCP responses with RoadAI data
   - Implement reasoning layer
   - Handle multi-source decision making

---