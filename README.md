# 🏃‍♂️ Runaway Buttons

Faz todos os botões da página **fugirem do cursor** quando você tenta clicar neles.  
Um troll visual leve e divertido.

---

## 💡 Como usar

1. Copie o código abaixo.  
2. Crie um novo favorito no navegador.  
3. Cole o código no campo de URL.  
4. Abra qualquer site e clique no favorito.

---

### 📜 Código

```javascript
javascript:(function(){
  if(window.__runawayActive){
    document.querySelectorAll('.runaway-btn').forEach(b=>b.style.transform='');
    window.__runawayActive=false;return;
  }
  window.__runawayActive=true;
  const buttons=document.querySelectorAll('button');
  buttons.forEach(btn=>{
    btn.classList.add('runaway-btn');
    btn.style.transition='transform 0.15s ease';
    btn.addEventListener('mousemove',e=>{
      const rect=btn.getBoundingClientRect();
      const x=e.clientX-rect.left-rect.width/2;
      const y=e.clientY-rect.top-rect.height/2;
      const dist=Math.sqrt(x*x+y*y);
      if(dist<100){
        const angle=Math.atan2(y,x);
        const moveX=-Math.cos(angle)*60;
        const moveY=-Math.sin(angle)*60;
        btn.style.transform=`translate(${moveX}px,${moveY}px)`;
      }else{
        btn.style.transform='translate(0,0)';
      }
    });
  });
  alert('Botões fujões ativados!');
})();
