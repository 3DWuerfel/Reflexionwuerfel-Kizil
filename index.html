<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D-Würfel mit Schattierungen</title>
    <style>
        body { margin: 0; }
        canvas { display: block; }
        #title { 
            position: absolute; 
            top: 10px; 
            width: 100%; 
            text-align: center; 
            color: white; 
            font-family: Arial, sans-serif; 
            font-size: 24px;
        }
        #info {
            position: absolute; 
            top: 50px; 
            width: 100%; 
            text-align: center; 
            color: white; 
            font-family: Arial, sans-serif; 
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div id="title">Reflexionswürfel by A. Kizil</div>
    <div id="info">Klick auf den Würfel oder tippe auf den Bildschirm zum Würfeln</div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // 3D-Szene, Kamera und Renderer einrichten
        let scene = new THREE.Scene();
        let camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        let renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(window.devicePixelRatio);  // HD-Auflösung
        renderer.shadowMap.enabled = true;  // Schatten aktivieren
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;  // Weiche Schatten
        document.body.appendChild(renderer.domElement);

        // Lichtquellen hinzufügen
        let ambientLight = new THREE.AmbientLight(0x404040, 1.5); // Umgebungslicht für weiches Licht
        scene.add(ambientLight);

        let pointLight = new THREE.PointLight(0xffffff, 1);  // Punktlicht für realistische Schatten
        pointLight.position.set(10, 10, 10);
        pointLight.castShadow = true;  // Schatten werfen
        pointLight.shadow.mapSize.width = 1024;  // Schattenauflösung
        pointLight.shadow.mapSize.height = 1024;
        scene.add(pointLight);

        // Raycaster und Maus-/Touch-Vektor für die Erkennung von Berührungen
        let raycaster = new THREE.Raycaster();
        let mouse = new THREE.Vector2();

        // Boden für Schattenwurf hinzufügen
        let planeGeometry = new THREE.PlaneGeometry(500, 500);
        let planeMaterial = new THREE.ShadowMaterial({ opacity: 0.3 });  // Transparentes Material für weichen Schatten
        let plane = new THREE.Mesh(planeGeometry, planeMaterial);
        plane.rotation.x = -Math.PI / 2;
        plane.position.y = -5;  // Unterhalb des Würfels
        plane.receiveShadow = true;  // Boden empfängt Schatten
        scene.add(plane);

        // Die Sätze für die Würfelseiten in Großbuchstaben
        let saetze = [
            "DAS WAR\nLEICHT",
            "DAS WAR\nSCHWER",
            "DAZU HABE ICH\nNOCH EINE FRAGE",
            "DAS MUSS\nICH NOCH ÜBEN",
            "DAS HAT MIR\nGEHOLFEN",
            "DAS HABE\nICH NEU GELERNT"
        ];

        // Material und Textur für die Würfelseiten erstellen
        let createTextTexture = function(text) {
            let canvas = document.createElement('canvas');
            canvas.width = 1024;  // Höhere Auflösung für den Text
            canvas.height = 1024;
            let context = canvas.getContext('2d');
            context.fillStyle = '#ffffff';
            context.fillRect(0, 0, canvas.width, canvas.height);
            context.fillStyle = '#000000';
            context.font = '80px Arial';  // Größere Schriftgröße
            context.textAlign = 'center';
            context.textBaseline = 'middle';

            // Mehrzeiliger Text in Großbuchstaben
            let lines = text.split('\n');
            lines.forEach((line, index) => {
                context.fillText(line, canvas.width / 2, (canvas.height / 2) - 50 + (index * 100));
            });

            return new THREE.CanvasTexture(canvas);
        };

        // Geometrie und Materialien für den Würfel
        let geometry = new THREE.BoxGeometry(3, 3, 3);  // Größerer Würfel
        let materials = saetze.map(sentence => new THREE.MeshStandardMaterial({ map: createTextTexture(sentence) }));
        let cube = new THREE.Mesh(geometry, materials);
        cube.castShadow = true;  // Der Würfel wirft Schatten
        scene.add(cube);

        // Position und Rotation der Kamera
        camera.position.z = 10;

        // Funktion, um den Würfel exakt auf eine Seite zu drehen (mit leichtem Neigungswinkel nach oben)
        let faceRotations = [
            { x: 0.2, y: 0, z: 0 },                   // Seite 1 (leicht nach oben geneigt)
            { x: 0.2, y: Math.PI / 2, z: 0 },         // Seite 2 (leicht nach oben geneigt)
            { x: 0.2, y: Math.PI, z: 0 },             // Seite 3 (leicht nach oben geneigt)
            { x: 0.2, y: -Math.PI / 2, z: 0 },        // Seite 4 (leicht nach oben geneigt)
            { x: Math.PI / 2 + 0.2, y: 0, z: 0 },     // Seite 5 (leicht nach oben geneigt)
            { x: -Math.PI / 2 + 0.2, y: 0, z: 0 }     // Seite 6 (leicht nach oben geneigt)
        ];

        let rolling = false;

        // Funktion, um den Würfel für eine zufällige Zeit zu rollen und dann in einem festen Neigungswinkel anzuhalten
        let randomizeRotation = function() {
            rolling = true;
            let randomIndex = Math.floor(Math.random() * 6);  // Zufällige Seite auswählen
            let rotation = faceRotations[randomIndex];        // Rotation der entsprechenden Seite (immer mit leichtem Neigungswinkel nach oben)
            
            // Startwerte für die Animation
            let rollTime = 1000; // Dauer des Rollens in Millisekunden
            let startTime = Date.now();

            let animateRoll = function() {
                let elapsed = Date.now() - startTime;

                // Würfel rotieren lassen (zufällige Bewegung während des Rollens)
                cube.rotation.x += 0.1;
                cube.rotation.y += 0.1;

                // Stoppe nach der festgelegten Zeit und richte die Rotation aus
                if (elapsed < rollTime) {
                    requestAnimationFrame(animateRoll);
                } else {
                    // Würfel auf die gewählte Seite einstellen (mit leichtem Neigungswinkel nach oben)
                    cube.rotation.set(rotation.x, rotation.y, rotation.z);
                    rolling = false;
                }
            };

            animateRoll();
        };

        // Funktion zum Starten des Würfelns
        let startRolling = function() {
            if (!rolling) {  // Nur würfeln, wenn der Würfel nicht schon rollt
                randomizeRotation();
            }
        };

        // Funktion zur Überprüfung, ob der Würfel getroffen wurde
        let checkIntersection = function(event) {
            if (event.touches && event.touches.length > 0) {
                // Für Touch-Events
                mouse.x = (event.touches[0].clientX / window.innerWidth) * 2 - 1;
                mouse.y = -(event.touches[0].clientY / window.innerHeight) * 2 + 1;
            } else {
                // Für Maus-Events
                mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
                mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;
            }

            // Raycaster von der Kamera aus werfen
            raycaster.setFromCamera(mouse, camera);

            // Prüfen, ob der Raycaster den Würfel trifft
            let intersects = raycaster.intersectObject(cube);

            if (intersects.length > 0) {
                startRolling();  // Würfeln, wenn der Würfel getroffen wurde
            }
        };

        // Render-Funktion
        let animate = function () {
            requestAnimationFrame(animate);
            renderer.render(scene, camera);
        };

        animate();

        // Event-Listener für Maus-Klicks
        window.addEventListener('click', checkIntersection);

        // Event-Listener für Touch-Events (für iPad und andere Touch-Geräte)
        window.addEventListener('touchstart', checkIntersection);
    </script>
</body>
</html>
