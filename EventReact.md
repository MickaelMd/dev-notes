### Les événements React sont utilisés en tant que props sur les éléments JSX. Leur nom suit une convention camelCase (par exemple : `onClick`, `onChange`), et leur valeur est une fonction qui sera appelée lorsque l'événement est déclenché.

**Exemple simple :**

```jsx

function App() {
  const handleClick = () => {
    alert("Bouton cliqué !");
  };

  return (
    <button onClick={handleClick>Cliquez-moi</button>
  );
}
  
```

**Utilisation avec des paramètres :**

Pour passer des arguments à une fonction dans un événement, encapsulez l’appel dans une fonction fléchée :

```jsx

function App() {
  const handleClick = (message) => {
    alert(message);
  };

  return (
    <button onClick={() => handleClick("Bonjour !")>
      Cliquez-moi
    </button>
  );
}
  
```

**Exemple avec un champ de formulaire :**

Utilisez des événements comme `onChange` pour capturer et gérer les valeurs des champs :

```jsx

function Form() {
  const [value, setValue] = React.useState("");

  const handleChange = (e) => {
    setValue(e.target.value);
  };

  return (
    <input 
      type="text" 
      value={value} 
      onChange={handleChange} 
      placeholder="Tapez ici" 
    />
  );
}
  
```

&nbsp;  
___


Voici une liste complète des événements React les plus courants basés sur les types d'interactions possibles. Ces événements sont utilisés comme props dans les composants React (par exemple : onClick, onChange, etc.).

### Événements de souris

*   **onClick** : Lorsqu'un élément est cliqué.
*   **onContextMenu** : Lorsqu'un clic droit ouvre le menu contextuel.
*   **onDoubleClick** : Lorsqu'un élément est double-cliqué.
*   **onMouseDown** : Lorsqu'un bouton de la souris est pressé.
*   **onMouseEnter** : Lorsqu'un curseur entre dans un élément.
*   **onMouseLeave** : Lorsqu'un curseur sort d'un élément.
*   **onMouseMove** : Lorsqu'un curseur se déplace à l'intérieur d'un élément.
*   **onMouseOut** : Lorsqu'un curseur quitte un élément.
*   **onMouseOver** : Lorsqu'un curseur passe au-dessus d'un élément.
*   **onMouseUp** : Lorsqu'un bouton de la souris est relâché.

### Événements de clavier

*   **onKeyDown** : Lorsqu'une touche est pressée.
*   **onKeyPress** : (Déprécié), préférez onKeyDown ou onKeyUp.
*   **onKeyUp** : Lorsqu'une touche est relâchée.

### Événements de formulaire

*   **onChange** : Lorsqu'une valeur change (par exemple, dans un champ texte ou une sélection).
*   **onInput** : Lorsqu'une entrée est effectuée (semblable à onChange, mais avec plus de granularité).
*   **onSubmit** : Lorsqu'un formulaire est soumis.
*   **onInvalid** : Lorsqu'un champ devient invalide.

### Événements de focus

*   **onFocus** : Lorsqu'un élément reçoit le focus.
*   **onBlur** : Lorsqu'un élément perd le focus.

### Événements de toucher (Touch)

*   **onTouchCancel** : Lorsqu'un point de contact est interrompu.
*   **onTouchEnd** : Lorsqu'un point de contact est relâché.
*   **onTouchMove** : Lorsqu'un point de contact est déplacé.
*   **onTouchStart** : Lorsqu'un point de contact commence.

### Événements de glissement (Pointer)

*   **onPointerDown** : Lorsqu'une interaction de pointeur commence.
*   **onPointerMove** : Lorsqu'un pointeur se déplace.
*   **onPointerUp** : Lorsqu'une interaction de pointeur se termine.
*   **onPointerCancel** : Lorsqu'une interaction de pointeur est annulée.
*   **onPointerEnter** : Lorsqu'un pointeur entre dans un élément.
*   **onPointerLeave** : Lorsqu'un pointeur sort d'un élément.
*   **onPointerOver** : Lorsqu'un pointeur passe au-dessus d'un élément.
*   **onPointerOut** : Lorsqu'un pointeur quitte un élément.

### Événements de composition (IME)

*   **onCompositionStart** : Lorsqu'une séquence de composition commence.
*   **onCompositionUpdate** : Lorsqu'une séquence de composition est mise à jour.
*   **onCompositionEnd** : Lorsqu'une séquence de composition se termine.

### Événements de sélection

*   **onSelect** : Lorsqu'une sélection de texte est faite.

### Événements de défilement (Scroll)

*   **onScroll** : Lorsqu'un élément est défilé.

### Événements de média

*   **onAbort** : Lorsqu'un téléchargement est annulé.
*   **onCanPlay** : Lorsqu'un média est prêt à être lu.
*   **onCanPlayThrough** : Lorsqu'un média peut être lu sans interruption.
*   **onDurationChange** : Lorsqu'une durée de média change.
*   **onEmptied** : Lorsqu'un média devient vide.
*   **onEnded** : Lorsqu'un média atteint sa fin.
*   **onError** : Lorsqu'une erreur se produit dans un média.
*   **onLoadedData** : Lorsqu'une donnée média est chargée.
*   **onLoadedMetadata** : Lorsqu'une métadonnée est chargée.
*   **onLoadStart** : Lorsqu'un média commence à se charger.
*   **onPause** : Lorsqu'un média est mis en pause.
*   **onPlay** : Lorsqu'un média commence à être lu.
*   **onPlaying** : Lorsqu'un média est en cours de lecture.
*   **onProgress** : Lorsqu'un téléchargement de média progresse.
*   **onRateChange** : Lorsqu'une vitesse de lecture change.
*   **onSeeked** : Lorsqu'un média atteint une position de recherche.
*   **onSeeking** : Lorsqu'une recherche dans un média commence.
*   **onStalled** : Lorsqu'un média est bloqué.
*   **onSuspend** : Lorsqu'un média est suspendu.
*   **onTimeUpdate** : Lorsqu'une position de temps de média est mise à jour.
*   **onVolumeChange** : Lorsqu'un volume de média change.
*   **onWaiting** : Lorsqu'un média attend des données.

### Événements de chargement (Load)

*   **onLoad** : Lorsqu'une ressource est chargée.
*   **onError** : Lorsqu'une ressource échoue à se charger.

### Événements de copier-coller

*   **onCopy** : Lorsqu'un contenu est copié.
*   **onCut** : Lorsqu'un contenu est coupé.
*   **onPaste** : Lorsqu'un contenu est collé.

### Événements de Drag & Drop

*   **onDrag** : Lorsqu'un élément est en cours de glissement.
*   **onDragEnd** : Lorsqu'un glissement se termine.
*   **onDragEnter** : Lorsqu'un élément glissé entre dans une cible.
*   **onDragExit** : Lorsqu'un élément glissé quitte une cible.
*   **onDragLeave** : Lorsqu'un élément glissé sort d'une cible.
*   **onDragOver** : Lorsqu'un élément glissé est maintenu au-dessus d'une cible.
*   **onDragStart** : Lorsqu'un glissement commence.
*   **onDrop** : Lorsqu'un élément est déposé.

### Événements de fenêtre

*   **onResize** : Lorsqu'une fenêtre ou un élément est redimensionné.
*   **onScroll** : Lorsqu'un défilement se produit.

### Événements personnalisés

Ces événements peuvent être créés avec des bibliothèques ou manuellement en utilisant `dispatchEvent`.

