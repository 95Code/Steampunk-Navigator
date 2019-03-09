# Blender Steampunk Kompass-Uhr
Als Projektarbeit in dem WPF Einführung in die Computergrafik habe ich zum Thema Steampunk einen Mix aus Uhr, Kompass und Navigationsgerät erstellt.

![Steampunk Navigator](kompassuhr_final_render.png)

# Tag 1 - Hintergrundbild
Am ersten Tag habe ich mir lediglich eine grobe Idee überlegt, was ich machen möchte und ein passendes Hintergrundbild gemacht.

- Hintergrundbild überlegen: Natur, altes Gebäude, Ziel für einen Wegweiser
- Foto machen: Kamera, Stativ, Bismarkturm

# Tag 2 - Meshes
Am zweiten Tag habe ich eine Skizze entworfen, das Objekt analysiert und den Großteil der Meshes erstellt. Außerdem habe ich die Beleuchtung installiert und die Kamera richtig positioniert.
Ich habe auf metrische Einheiten verzichtet und verwende Blender Units.

## Skizze
Ich habe auf dem Foto eine grobe Skizze gemacht, wie mein Objekt später aussehen soll, damit ich weiß, was ich eigentlich modelieren muss. Der rot eingezeichnete Bogen stellte sich in der Umsetzung leider als zu kompliziert heraus.

## Analyse
Aus welchen Objekten besteht das Model?

- Zylinder aus Rand, Torusen und Boden
- Uhr aus Ziffern, Platte Zeigern und Zahnrädern
- Kompass aus Buchstaben, Platte und Zahnrädern
- Kurbeln aus Spirale und Griffen
- Kuppel aus Glas

## Zylinder
- Kreis mit Radius 5 und 64 Segmenten, in z-Richtung auf Höhe 3 extruden.
- Oben und unten ein Torus mit major Radius 5 und 64 Segmenten sowie minor Radius 0,16 und 12 Segmente.
- Für die Griffe und Kurbeln habe ich in den Zylinder Löcher gestempelt.

## Uhr
- Mit dem neuen Wissen kann ich die Ziffern als Text-Objekte in Blender einfügen und bearbeiten.
- Die Ziffern sind entlang eines Kreises auf dem Ziffernblatt angeordnet. Sie haben eine Höhe von 0,05 und eine Tiefe von 0,025.
- Die Ziffern liegen auf einer Kreisplatte die aus zwei Zylindern und dem Difference-Modifier erstellt wurde. Die Dicke dieser Platte beträgt 0,1.

## Kompass
Der Kompass war zunächst mit den Buchstaben N, O, S und W beschriftet. Doch da ich keinen, wie in der Skizze mit rot eingezeichnten 3. Zeiger modelieren werde, bekommt der Kompass einen Pfeil und den Schriftzug "Ziel".

## Zeiger
Stunden- und Minutenzeiger sind ohne Modifier modelliert, da ich es als schneller empfand, es per Hand zu machen. Ein Mirrormodifier wäre im Nachhinein aber schneller gewesen.

## Glaskuppel
Die Glaskuppel besteht aus 2 Sphären, die ineinander liegen. Die untere Hälfte ist abgeschnitten. An der Schnittkante sind sie wieder mit einem Torus zusammengefügt.

## Kurbel
Die Kompassuhr hat 4 Kurbeln, an denen die Mechanik eingestellt und aufgespannt werden kann.
Die Kurbeln sollen mit einer Spirale in den Zylinder führen. Dazu verwende ich den Screw Modifier.
Der Griff der Kurbeln besteht aus einem Kegel, der mit dem Mirror-Modifier gespiegelt ist. An den Enden befinden sich Toruse, welche die Kanten abrunden. In der Mitte ist ebenfalls ein Torus angebracht.

## Zahnräder
Mit dem Extras Addon kann ich Zahnräder einfügen.

- Der Zielring wird durch ein eingestempeltes Zahnrad beweglich.
- Die Zeiger sind mit einem Zahnrad verbunden und werden jeweils mit einem weitern Zahnrad gesteuert.

## Verzierungen
Auf dem Ring der Ziffern und dem Kompassring habe ich Schrauben angebracht. Ebenso sind an der Außenseite des Zylinders kleine Nieten.
Diese Objekte habe ich mit Hilfe eines Array- und Curve-Modifiers erstellt.

## Kamera
- Der Kamera wird über den Node-Editor das Hintergrundbild gegeben. Sie wird dann so eingestellt, dass die Kompassuhr richtig positioniert ist.

## Beleuchtung
Auf dem Foto ist zu erkennen, dass es sehr wolkig ist. Das ist gut für mich, da als Licht einfach eine große weiße Softbox über der ganzen Szene genutzt werden kann.


# Tag 3 - Schatten und Materialien
Den dritten Tag war ich sehr beschäftigt mit einem korrekten Schattenwurf auf meiner Hand auf dem Foto und realistischen Materialien.

## Schattenwurf
Damit ich auf meiner Hand auf dem Foto einen Schatten habe, habe ich meine Hand mit einer Pane nachmodelliert. Auf diesem Model ist dann der Schatten der Kompassuhr zu sehen.
Blender rendert dann insgesamt 3 Ebenen. Auf der ersten Ebene ist nur das Model selbst zu sehen. Auf der Zweiten die nachmodellierte Hand mit dem Schatten und auf der Dritten nur die nachmodellierte Hand ohne Schatten.
Mit verschiedenen Nodes wird dann von der Zweiten die Erste Ebene abgezogen. Das wird wiederum auf den Hintergrund gelegt und darauf die erste Ebene mit dem Model gesetzt.

## Materialien
Ich brauche folgende Materialien

- Gold für Außenseite und Schrift
- Silber für Zeiger und Kompassplatte
- Eisen für Griffe Zahnräder
- Kupfer für Schrauben und Nieten
- Marmor für das Ziffernblatt
- Glas für die Kuppel

Ich habe die korrekten Farbwerte für Metalle aus meinen Quellen übernommen und mit dem Wissen aus den Blender-Guru Tutorials physikalisch korrekt rendernde Nodes erstellt (PBR Materials).

# Quellen

## Text
Das Ziffernblatt ist nicht wie bei einer gewöhnlichen Uhr im Dezimalsystem, sondern im Duodezimalsystem (12er) dargestellt. Dazu musste ich mir beibringen, wie man Text als Objekt hinzufügt und eine Schriftart hinzufügt, welche die Zeichen für 10 und 11 enthält.

- [Wikipedia - Duodezimalsystem](https://de.wikipedia.org/wiki/Duodezimalsystem)
- [Unicode Fonts for Ancient Scripts](http://users.teilar.gr/~g1951d/)
- [YouTube - Blender Schriftart ändern](https://www.youtube.com/watch?v=MYYQocMbiAM)
- [blenderartists.org - [SOLVED] Unicode / Special characters in Blender 2.6](https://blenderartists.org/forum/showthread.php?274552-Unicode-Special-characters-in-Blender-2-6)
- [gamefromscratch.com - Creating and rendering text in Blender](http://www.gamefromscratch.com/post/2015/01/12/Creating-Text-in-Blender.aspx)
- [blenderartists.org - Converting Text to Mesh](https://blenderartists.org/forum/showthread.php?62339-Converting-Text-to-Mesh)

## Materialien
Die Kompass-Uhr soll aus verschiedenen Materialien bestehen. Dazu muss ich mir noch etwas mehr Wissen aneignen.

- [YouTube - Blender Cycles tutorial: Creating realistic glass](https://www.youtube.com/watch?v=l_0McbTNH8I)
- [YouTube - Blender Guru - How to Make Photorealistic PBR Materials - Part 1 ](https://youtu.be/V3wghbZ-Vh4)
- [YouTube - Blender Guru - How to Make Photorealistic Materials - Part 2: Metal](https://youtu.be/m1PkSViBi-M)

## Texturen und Schriften
In dem Projekt wird nur eine Marmor-Textur für das Ziffernblatt verwendet.

- [poliigon - Free Textures - Marble 062](https://www.poliigon.com/texture/2186)

## Schatten
In diesem Tutorial wird ausführlich erklärt, wie man auf einem Hintergrundbild nur den Schatte eines Objektes rendert.

- [YouTube - Tutorial: Cycles Shadows Only: Shadow Catcher](https://www.youtube.com/watch?v=k7gKzgvFiGM)

## Sonstiges
Sonstige Unklarheiten habe ich dank der folgenden Quellen beseitigen können.

- [BlenderWiki - Gear Addon](https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Add_Mesh/Add_Gear)
- [StackExchange - Setting the pivot point of an object](https://blender.stackexchange.com/questions/5519/setting-the-pivot-point-of-an-object)
- [blender.org - Navigation: Camera View](https://docs.blender.org/manual/en/dev/editors/3dview/navigate/camera_view.html)
- [Unicode Zeichentabelle - Pfeile](https://unicode-table.com/de/sets/arrows-symbols/)
