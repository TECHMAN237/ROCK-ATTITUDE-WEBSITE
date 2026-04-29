# Solution de fond Spline (Transparence et Logo)

## Problème : Fond noir persistant
Les animations Spline intégrées par `<iframe>` affichent souvent un fond noir malgré l'option "Hide Background" dans l'éditeur.

## Solution Technique : Le mix-blend-mode (Méthode Claude)
Cette méthode consiste à "filtrer" le noir de l'iframe directement en CSS.

### 1. Structure HTML recommandée
Placer l'iframe dans un conteneur `absolute` placé au début du bloc parent (ex: `hero section`) pour qu'il se mélange correctement avec l'image de fond.

```html
<div class="absolute inset-0 z-0 pointer-events-none flex items-center justify-center" 
     style="mix-blend-mode: screen;">
  <div class="w-full h-[70vh] overflow-hidden">
    <iframe src="VOTRE_LIEN_SPLINE" 
            frameborder="0" 
            style="width: 100%; height: 100%; background: transparent;" 
            allowtransparency="true"></iframe>
  </div>
</div>
```

### 2. Propriété CSS Critique
- `mix-blend-mode: screen;` : C'est l'instruction qui rend le noir transparent.
- `pointer-events-none` : Indispensable pour que l'animation ne bloque pas les clics sur les boutons du site situés en dessous.

## Retirer le logo "Built with Hana / Spline"
Si vous n'avez pas de compte payant, le logo peut être masqué techniquement en "rognant" le bas de l'iframe avec un `clip-path` ou un conteneur avec `overflow: hidden`.

```css
/* Exemple de rognage du bas de l'iframe (environ 50px) */
iframe {
  clip-path: inset(0 0 50px 0);
}
```

---
*Note : Cette solution a été validée avec succès sur le projet Mika.*
