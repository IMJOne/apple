![apple](https://user-images.githubusercontent.com/110226567/213878791-c39e31ca-01e6-4728-b8b9-9374b6249ba0.png)

# π Apple

Apple iPad μ ν μκ° νμ΄μ§ π [Demo](https://imjone.github.io/apple/)

<br />

## π’ νλ‘μ νΈ κ°μ

Apple μΉμ¬μ΄νΈμμ μμ£Ό μ¬μ©λλ κ³ κΈ μΈν°λμ κΈ°λ² ν΄λ‘  μ½λ© μ¬μ΄νΈμλλ€.<br />
μ€ν¬λ‘€κ°μ μ΄μ©ν ν€νλ μ λ° μΊλ²μ€λ₯Ό νμ©ν λ€μν μ λλ©μ΄μμ΄ κ΅¬νλμ΄ μμ΅λλ€.<br />
λμ  μμλ₯Ό κ·Ήλννμ¬ μΉ νλ‘μ νΈλ₯Ό λνν  μ μλ νλ €ν μ¬μ΄νΈλ₯Ό λ§λ€μ΄λ³΄κ³ μ μ μνκ² λμμ΅λλ€.

<br />

## π¨οΈ μ¬μ© κΈ°μ 

<p>
  <img src="https://img.shields.io/badge/HTML-e34f26?style=flat-square&logo=HTML5&logoColor=white"/>
  <img src="https://img.shields.io/badge/CSS-1572b6?style=flat-square&logo=CSS3&logoColor=white"/>
  <img src="https://img.shields.io/badge/JavaScript-f7df1e?style=flat-square&logo=JavaScript&logoColor=white"/>
</p>

<br />

## π μ£Όμ κΈ°λ₯

- κ³ μ λ μμΉμμ μ§μ λ νμ΄λ°μ λ±μ₯νλ νμ€νΈ
- μ€ν¬λ‘€κ°μ λ°λΌ μ μ΄λλ κ³ ν΄μλ λΉλμ€ μΈν°λμ
- μ΄λ―Έμ§ λΈλ λ© λ° μΊλ²μ€ μ€μΌμΌ λλ‘μ° μ λλ©μ΄μ
- μ€ν¬λ‘€μ λ°μνμ¬ λ°°κ²½μ΄ λΈλ¬ μ²λ¦¬λλ λ©λ΄λ°
- svg νκ·Έμ css keyframeμ νμ©ν λ‘λ© μ€νΌλ

<br />

## π» μμ€ μ½λ

μ μ²΄ μ½λ λ³΄λ¬ κ°κΈ° π [Notion](https://imjone.notion.site/Apple-ba7b279ed3c643eb88a3439cb004d3c3)

### π μ λλ©μ΄μ μ λ³΄ κ°μ²΄ λ°°μ΄ μ μ

μ λλ©μ΄μκ³Ό κ΄λ ¨λ μ λ³΄λ₯Ό λ΄μ λ°°μ΄μ λ―Έλ¦¬ μ μν΄λμμ΅λλ€.<br />
μΈνλ  λμ΄ κ° λ° μ λλ©μ΄μ μμ μ§μ , μ’λ£ μ§μ  λ±μ΄ ν΄λΉλ©λλ€.

```javascript
const sceneInfo = [
  {
    type: 'sticky',
    heightMultiple: 5,
    scrollHeight: 0,
    objs: {
      container: document.querySelector('#scroll-section-3'),
      canvasCaption: document.querySelector('.canvas-caption'),
      canvas: document.querySelector('.image-blend-canvas'),
      ctx: document.querySelector('.image-blend-canvas').getContext('2d'),
      imagesPath: ['img/blend-image-1.jpg', 'img/blend-image-2.jpg'],
      images: [],
    },
    values: {
      rect1X: [0, 0, { start: 0, end: 0 }],
      rect2X: [0, 0, { start: 0, end: 0 }],
      rectStartY: 0,
      blendHeight: [0, 0, { start: 0, end: 0 }],
      canvas_scale: [0, 0, { start: 0, end: 0 }],
      canvasCaption_opacity: [0, 1, { start: 0, end: 0 }],
      canvasCaption_translateY: [20, 0, { start: 0, end: 0 }],
    },
  },
  ...
];
```

### π μ λλ©μ΄μ κ³μ° ν¨μ

μ λλ©μ΄μ μ λ³΄μ νμ¬ μ€ν¬λ‘€κ°μ μΈμλ‘ μ λ¬νμ¬ νΈμΆνλ©΄,<br />
μ λλ©μ΄μ μ€ν μ λ³νλ  κ°λ€μ κ³μ°νμ¬ λ¦¬ν΄ν΄μ£Όλ ν¨μμλλ€.

```javascript
function calcValues(values, currentScrollY) {
  let value;

  // νμ¬ μΉμμμ μ€ν¬λ‘€ λ κ°μ λ²μλ₯Ό λΉμ¨λ‘ κ΅¬νκΈ°
  const scrollHeight = sceneInfo[currentScene].scrollHeight;
  const scrollRatio = currentScrollY / scrollHeight;

  if (values.length === 3) {
    // start ~ end : μ λλ©μ΄μ κ΅¬κ°
    const partScrollStart = values[2].start * scrollHeight; // μ λλ©μ΄μ μμ μ§μ 
    const partScrollEnd = values[2].end * scrollHeight; // μ λλ©μ΄μ λλλ μ§μ 
    const partScrollHeight = partScrollEnd - partScrollStart;

    // μ λλ©μ΄μ κ΅¬κ° μ§μ μμλ§ μ λλ©μ΄μ μ€ν
    if (currentScrollY >= partScrollStart && currentScrollY <= partScrollEnd) {
      value = ((currentScrollY - partScrollStart) / partScrollHeight) * (values[1] - values[0]) + values[0];
    } else if (currentScrollY < partScrollStart) {
      value = values[0];
    } else if (currentScrollY > partScrollEnd) {
      value = values[1];
    }
  } else {
    // νμ¬ μΉμμμ μ€ν¬λ‘€ λ κ°μ λΉμ¨ * μ λλ©μ΄μ μ§ν λ²μ + μ΄κΈ°κ° (μ λλ©μ΄μμ΄ μμ μ§μ )
    value = scrollRatio * (values[1] - values[0]) + values[0];
  }
  return value;
}
```

### π μ λλ©μ΄μ μ€ν ν¨μ

νμ¬ μΉμμμμ μ€ν¬λ‘€κ°μ κ΅¬νμ¬ `calcValues` ν¨μλ₯Ό νΈμΆνκ³ ,<br />
λ¦¬ν΄λ κ°μ ν λλ‘ κ° μΉμμ λ§λ CSS μ€νμΌμ μ μ©ν΄μ£Όλ ν¨μμλλ€.

```javascript
function playAnimation() {
  const objs = sceneInfo[currentScene].objs;
  const values = sceneInfo[currentScene].values;
  const currentScrollY = scrollY - prevScrollHeight; // νμ¬ μΉμμμμ μ€ν¬λ‘€κ°
  const scrollHeight = sceneInfo[currentScene].scrollHeight;
  const scrollRatio = currentScrollY / scrollHeight; // currentScrollYλ₯Ό λΉμ¨λ‘ λνλΈ λ³μ

  switch (currentScene) {
    case 0:
      objs.ctx.drawImage(objs.images[0], 0, 0);
      objs.canvas.style.opacity = calcValues(values.canvas_opacity, currentScrollY);

      if (scrollRatio <= 0.22) {
        // in
        objs.messageA.style.opacity = calcValues(values.messageA_opacity_in, currentScrollY); // 0 ~ 1
        objs.messageA.style.transform = `translateY(${calcValues(values.messageA_translateY_in, currentScrollY)}%)`; // 20 ~ 0
      } else {
        // out
        objs.messageA.style.opacity = calcValues(values.messageA_opacity_out, currentScrollY); // 1 ~ 0
        objs.messageA.style.transform = `translateY(${calcValues(values.messageA_translateY_out, currentScrollY)}%)`; // 0 ~ -20
      }
      break;
      ...
  }
}
```

<br />

## π λ°°μ΄ μ  λ° λλ μ 

- λμ΄λ μλ μΈν°λν°λΈ μΉ κ°λ°μ λν λμ΄ μ‘°κΈμ νΈμΈ κ² κ°μ΅λλ€.
- ν΅μ¬ κΈ°λ₯μ λν μμ΄λμ΄λ₯Ό κ΅¬ννκ³  λ³΅μ‘ν μμΉ λ° ν¬κΈ° κ³μ° μ°μ΅μ ν΄λ³Ό μ μμμ΅λλ€.
- λ³λμ λΌμ΄λΈλ¬λ¦¬ μ¬μ© μμ΄ μλ¦¬μ μκ°νμ¬ μ€ν¬λ‘€ μΈν°λμ κ΅¬ν κ³Όμ μ μ΄ν΄ν  μ μμμ΅λλ€.
