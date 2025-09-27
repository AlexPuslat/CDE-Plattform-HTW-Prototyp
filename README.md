# CDE-Plattform-HTW-Prototyp
Diese Anwendung ist Bestandteil der Masterarbeit von Alexander Puslat zu Thema "Entwicklung einer Open Source-basierten CDE-Plattform für digitale Zwillinge im gebäudetechnischen Energiemanagement".
# CDE-Plattform HTW Berlin

> **Digitaler Zwilling im gebäudetechnischen Energiemanagement**  
> Version 1.0 von Alexander Puslat

Eine Open Source Common Data Environment (CDE) Plattform für die Visualisierung und das Monitoring von BIM-Modellen mit Echtzeitdatenintegration.

##  Über das Projekt

Diese CDE-Plattform wurde als Teil einer Forschungsarbeit an der HTW Berlin entwickelt und implementiert einen digitalen Zwilling für gebäudetechnisches Energiemanagement. Die Anwendung ermöglicht die Integration von IFC-Modellen mit Live-Sensordaten aus der Gebäudeleittechnik.

### Hauptfunktionen

- **IFC-Viewer**: 3D-Visualisierung von BIM-Modellen im Browser
- **Sensordatenmonitoring**: Echtzeitüberwachung von Gebäudesensoren
- **Zeitreihendarstellung**: Analyse von Sensordaten über Zeit
- **Geometrische Verortung**: Live-Daten werden direkt im 3D-Modell verortet

##  Technologie-Stack

### Frontend
- **Streamlit 1.28.0** - Web-Interface und Benutzerinteraktion
- **IFC.js 1.5.0** - IFC-Datei-Verarbeitung im Browser
- **Three.js r128** - 3D-Rendering und Visualisierung

### Backend
- **Flask 2.3.0** - REST API für Datenverarbeitung
- **Python 3.9.13** - Serverlogik
- **SQLite 3.42.0** - Lokale Datenbank
- **IFCOpenShell 0.7.0** - IFC-Datenverarbeitung

## 📋 Systemanforderungen

### Mindestanforderungen
- **Prozessor**: Intel i7 oder vergleichbar
- **RAM**: 16GB
- **Betriebssystem**: Windows 11, macOS, Linux
- **Browser**: Chrome, Firefox, Safari, Edge (mit JavaScript-Unterstützung)

### Unterstützte Formate
- **IFC-Dateien**: .ifc (IFC 4.0 Standard)
- **Maximale Dateigröße**: 200MB
- **Kompatibilität**: 95% Funktionserfüllung des IFC 4.0 Standards

##  Installation

### 1. Repository klonen
```bash
git clone https://github.com/[username]/cde-plattform-htw.git
cd cde-plattform-htw
```

### 2. Python-Umgebung einrichten
```bash
# Virtuelle Umgebung erstellen
python -m venv venv

# Aktivieren (Windows)
venv\Scripts\activate

# Aktivieren (macOS/Linux)
source venv/bin/activate
```

### 3. Dependencies installieren
```bash
pip install -r requirements.txt
```

### 4. Anwendung starten

#### Streamlit Frontend starten
```bash
streamlit run Startseite.py
```

#### Flask Backend starten (separates Terminal)
```bash
python app.py
```

##  Projektstruktur

```
cde-plattform-htw/
├── Startseite.py           # Haupteinstiegspunkt
├── app.py                  # Flask Backend Server
├── pages/                  # Streamlit Seiten
│   ├── IFC-Viewer.py      # 3D-Viewer Komponente
│   └── ...
├── frontend-viewer/        # IFC.js Frontend Komponenten
│   ├── main.js            # Three.js Integration
│   ├── GLTFLoader.js      # 3D-Model Loading
│   └── vendor/            # Externe Bibliotheken
├── static/                 # Statische Dateien
│   └── models/            # IFC-Beispieldateien
├── requirements.txt        # Python Dependencies
└── README.md              # Diese Datei
```

## 🔧 Konfiguration

### Sensordaten-API
Die Anwendung verbindet sich mit der HTW OpenWeb API:
```
Basis-URL: https://openweb.f1.htw-berlin.de
API-Endpunkt: /api/v1/trend/datapoints/{sensor_id}/data
```

### Authentifizierung
API-Schlüssel werden über Umgebungsvariablen konfiguriert:
```bash
export HTW_API_KEY="your_api_key_here"
```

##  Funktionalitäten

### IFC-Datenverarbeitung
- Vollständige IFC 4.0 Standardunterstützung
- Automatische Entitätserkennung und -klassifikation
- Semantische Attributextraktion
- 3D-Geometriedarstellung

### Sensordatenintegration
- Echtzeitdatenabfrage über REST API
- Automatische Sensor-zu-Geometrie-Zuordnung
- Visualisierung mit konfigurierbaren Schwellwerten
- Historische Datenanalyse

### Performance
- Optimiertes Raycasting für 3D-Interaktion
- Effiziente IFC-Parsing-Pipeline
- Clientseitiges Rendering mit Three.js

##  Verwendung

### 1. IFC-Datei hochladen
1. Öffnen Sie die Anwendung im Browser
2. Klicken Sie auf "BROWSE" in der Sidebar
3. Wählen Sie eine IFC-Datei (max. 200MB)
4. Warten Sie auf die Verarbeitung

### 2. 3D-Viewer nutzen
1. Navigieren Sie zu "IFC-Viewer" in der Sidebar
2. Verwenden Sie Maus/Touchpad für Navigation:
   - **Rotieren**: Linke Maustaste + Ziehen
   - **Zoomen**: Mausrad
   - **Verschieben**: Rechte Maustaste + Ziehen

### 3. Sensordaten überwachen
1. Öffnen Sie "Sensordatenmonitoring"
2. Sensoren werden automatisch im 3D-Modell platziert
3. Live-Werte werden in Echtzeit aktualisiert

##  Bekannte Limitationen

- **Komplexe Geometrien**: Ladezeiten >30 Sekunden bei sehr großen Modellen
- **Browser-Storage**: Keine Verwendung von localStorage/sessionStorage
- **Drei.js Version**: Begrenzt auf r128 (CapsuleGeometry nicht verfügbar)

##  Entwicklung

### Entwicklungsumgebung
- **IDE**: Visual Studio Code empfohlen
- **Testing**: Getestet auf Alienware m15 R7 (Intel i7-12700H, 16GB RAM)
- **Browser-Testing**: Chrome, Firefox, Safari, Edge

### Code-Stil
- Python: PEP 8 Konventionen
- JavaScript: ES6+ Standards
- IFC.js: Three.js Best Practices

##  Architektur

Die Anwendung folgt einer modularen Webarchitektur mit klarer Trennung zwischen:

1. **Frontend** (Streamlit + IFC.js): Benutzerinteraktion und 3D-Visualisierung
2. **Backend** (Flask): Datenverarbeitung und API-Integration
3. **Datenebene** (SQLite): Lokale Datenpersistierung

![Systemarchitektur](docs/system-architecture.png)

##  Beitragen

Beiträge sind willkommen! Bitte beachten Sie:

1. Forken Sie das Repository
2. Erstellen Sie einen Feature-Branch
3. Committen Sie Ihre Änderungen
4. Erstellen Sie einen Pull Request

##  Lizenz

Dieses Projekt ist vollständig Open Source und unter der [MIT Lizenz](LICENSE) verfügbar.

## 🎓 Akademischer Kontext

Diese Arbeit wurde im Rahmen einer Forschungsarbeit an der HTW Berlin entwickelt und leistet einen praktischen Beitrag zur Demokratisierung digitaler Zwillings-Technologien durch systematische Evaluation und Integration verfügbarer Open Source Komponenten.

### Wissenschaftlicher Beitrag
- Systematische Analyse von Open Source CDE-Komponenten
- Praktische Implementierung dreidimensionaler CDE-Architektur
- Demonstration der Integration von BIM und IoT-Daten
- Evaluierung von Systemgrenzen und Limitationen

##  Kontakt

**Alexander Puslat**  
HTW Berlin  
[alexander.puslat@student.htw-berlin.de](mailto:alexander.puslat@student.htw-berlin.de)

## 🙏 Danksagungen

- HTW Berlin für die Forschungsunterstützung
- IFCOpenShell Community
- Three.js Entwicklerteam
- Streamlit Team

---

**🚧 Hinweis**: Diese Plattform befindet sich in aktiver Entwicklung. Für Produktionsumgebungen wird eine umfassende Sicherheitsevaluierung empfohlen.
