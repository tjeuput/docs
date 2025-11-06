Mit der Einführung des neuen WYSIWYG-Editors CKEditor 5 (CK5) für E-Mail-Vorlagen und Templates in infokop Base 4.2.0 ergeben sich mehrere unerwünschte Verhaltensweisen im Zusammenhang mit Links:

- Bei Links (z. B. normale Hyperlinks oder QR-Code-verknüpfte Links) erscheint bei Mouse-Over beim bearbeiten des Links standardmäßig der Hinweis „**Link in neuem Tab öffnen**“.
    
- Dies ist in unserer Umgebung nicht möglich, da durch unsere Infoskop-Monitor-Umgebung und deren Sicherheitskonzept (IM Restriktion) das Öffnen von neuen Tabs über das Webfrontend nicht erlaubt ist.
    
- Auch ein direkter Klick auf den Link im Editor führt nicht zur Öffnung im Standardbrowser – es passiert nichts.
    
- Lediglich beim Setzen eines Links über den Formularlink-Dialog funktioniert das Link-Ziel erwartungsgemäß.
    

**Schritte zur Reproduktion:**

1. Öffne eine E-Mail-Vorlage in infoskop Base 4.2.0.
    
2. Füge einen Link und/oder QR-Code mit Link hinzu über Formularlink.
    
3. Bearbeite den eingefügten Link.
    
4. Bewege die Maus über den Link – der Hinweis „Link in neuem Tab öffnen“ erscheint.
    
5. Klicke den Link an – es erfolgt keine Reaktion.