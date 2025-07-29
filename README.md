
# 🚦 TrafficScript

**TrafficScript** is a lightweight, human-readable **Domain-Specific Language (DSL)** for the **rapid prototyping of urban traffic scenarios**. It allows researchers, engineers, and educators to define roads, vehicles, signals, and events using a minimal syntax, and export these scenarios directly to simulation platforms like **SUMO**, **MATSim**, and (optionally) **Nocturne**.

---

## ✨ Features

- 📜 Simple, declarative DSL syntax inspired by natural language  
- 🛣️ Define roads, lanes, signals, vehicles, and events  
- 🧩 Scenario-based modeling with triggers (time, environment, relative entity) actions  
- 🔁 Support for signal phases, spawn timing, and vehicle routes
- 🔄 Multi-backend support: `SUMO`, `MATSim`, and planned `Nocturne` integration  
- 📦 CLI tools to convert `.dsl` files into simulation-ready XMLs  
- 📚 Built for teaching, workshops, and research prototyping.

---

## 🚀 Quick Example

```dsl
scenario "SimpleIntersection" {
    road main_road length 250m lanes 2 direction bidirectional;
    road side_road length 150m lanes 1 direction bidirectional;

    vehicle car_1 type passenger spawn at 5s route main_road -> side_road;
    vehicle car_2 type passenger spawn at 15s route side_road -> main_road;

    signal intersection_light location main_road_x_side_road {
        phase green 30s;
        phase yellow 5s;
        phase red 30s;
    }
}
```

---

## 🧠 Why TrafficScript?

Existing tools like SUMO and MATSim require verbose XML or complicated toolchains for scenario generation. TrafficScript:

- Reduces friction in creating test cases  
- Enables **rapid iteration**  
- Integrates easily into simulation workflows  
- Encourages learning and experimentation through clarity  

---

## 📂 Project Structure

```
traffic-script/
├── parser/
│   ├── grammar.lark         # Lark parser grammar definition
│   └── parser.py            # AST and parsing logic
├── examples/
│   ├── SimpleIntersection.dsl
│   └── PedestrianEvent.dsl
├── generators/
│   ├── sumo_generator.py    # Generates SUMO XML files
│   └── matsim_generator.py  # Generates MATSim files
├── scripts/
│   └── compile.py           # CLI wrapper for translation
├── README.md
└── requirements.txt
```

---

## ⚙️ Installation

```bash
git clone https://github.com/yourusername/traffic-script.git
cd traffic-script
pip install -r requirements.txt
```

---

## 📥 Usage

```bash
python scripts/compile.py --input examples/SimpleIntersection.dsl --backend sumo
```

---

## 🧪 Supported Backends

- ✅ SUMO (network, route, config generation)  
- ✅ MATSim (network.xml, population.xml, config.xml)  
- 🔜 Nocturne (planned support)  

---

## 📚 Background

TrafficScript builds upon ideas from:
- **ASAM OpenSCENARIO / OpenDRIVE**
- **Athos DSL** (Hoffmann et al.)
- **Eclipse MOSAIC**, **SUMO**, **MATSim**

It is designed for developers, researchers, and students working in:
- Traffic simulation
- ADAS validation
- Intelligent transportation systems
- Smart cities and digital twins

---

## 👨‍🔬 Author

**Idrees Muhammad**  
ADAS Simulation Engineer
[LinkedIn](https://www.linkedin.com/in/midrees321)

---

## 📄 License

MIT License
