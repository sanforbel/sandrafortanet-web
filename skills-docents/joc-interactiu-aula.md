---
name: joc-interactiu-aula
description: >-
  Convertix qualsevol contingut (un tema, un text, vocabulari, una unitat) en un joc interactiu HTML per a l'aula, en un sol fitxer que s'obri al navegador, es projecta a la pissarra digital o s'incrusta a Google Sites o a la plataforma del centre: qüestionari amb mode equips, memory de parelles o escape room amb proves encadenades. Adapta el nivell a l'etapa (Infantil, Primària, ESO, Batxillerat, FP) i no envia cap dada a internet. Usa-la sempre que un docent diga "fes-me un joc", "un quiz", "un kahoot", "un trivial", "un escape room", "un memory", "gamifica este tema", "un repàs divertit", "un juego para clase", o vulga repassar continguts d'una manera interactiva.
---
# Joc interactiu per a l'aula

> **Versió d'un sol fitxer.** Quan el text esmenta `references/…`, el contingut és als annexos del final d'este document, i la plantilla del joc també (annex E). Si no pots executar codi, substituïx a mà `__DADES_JSON__` i `__TITOL__`.

El joc funciona quan el contingut és rigorós i la dinàmica és senzilla: una pantalla clara, botons grans i un motiu per a jugar en equip. La plantilla ja resol la part tècnica; el teu treball és fer preguntes bones.

Llig l'apartat de l'etapa de `references/etapes.md`, `references/llengua.md` i `references/privacitat.md`.

## Flux
1. Recull (una sola tanda, amb botons si n'hi ha):
   - etapa i curs;
   - contingut (que l'enganxe o l'adjunte, o el tema i el que han de saber);
   - tipus de joc: **qüestionari** (recomanat per a repassar), **memory** (vocabulari, conceptes i definicions, parelles), **escape room** (repte final d'unitat);
   - nombre d'ítems (per defecte: 10 preguntes, 8 parelles o 5 proves) i llengua.
2. Crea el contingut i genera el fitxer.
3. Comprova'l i entrega'l.

## Generar el fitxer
1. Escriu un JSON amb l'estructura documentada a la plantilla (`assets/plantilla-joc.html`, comentari "Format"):
   - `quiz`: `preguntes` amb `pregunta`, `opcions` (3-4), `correcta` (índex des de 0) i `explicacio` breu.
   - `memory`: `parelles` com a llistes de dos textos curts (màxim 12).
   - `escape`: `proves` amb `narrativa`, `enigma`, `resposta` (text o llista de respostes acceptades) i `pista`.
   - `titol`, `subtitol`, `final`, `peu` (per exemple, el nom del docent o del centre si el vol) i `llengua` (`ca` o `es`).
2. Executa `python3 scripts/genera_joc.py dades.json nom-del-joc.html`. L'script valida les dades i avisa si n'hi ha alguna malament.
   Si l'entorn no pot executar codi, fes-ho a mà: copia la plantilla sencera i substituïx `__DADES_JSON__` pel JSON i `__TITOL__` pel títol. Revisa tu mateix que cada `correcta` siga un índex vàlid.
3. Si l'entorn permet publicar o previsualitzar pàgines (artefactes, canvas o similar), publica-la perquè el docent tinga un enllaç; si no, entrega el fitxer .html.

Si el docent vol un tipus de joc que la plantilla no fa (ordenar, classificar, ruleta, sopa de lletres…), construïx-lo en un sol fitxer HTML seguint les mateixes regles: sense dependències externes, botons d'almenys 48 px, contrast alt, tema clar i fosc, i tot en una pantalla de mòbil o de pissarra.

## Qualitat del contingut
- **Qüestionari**: una sola resposta correcta i inequívoca; distractors plausibles que revelen errors típics (no absurds); l'explicació diu per què, en una frase. Barreja preguntes de record, comprensió i aplicació.
- **Memory**: textos de 1-6 paraules per carta, perquè es lligen de lluny.
- **Escape room**: una narrativa breu que lliga les proves; cada resposta és una paraula o un número fàcil d'escriure (accepta variants amb i sense accents, la plantilla ja normalitza majúscules i accents).
- Contingut correcte i contrastat. Si el docent n'aporta un text, només preguntes que es puguen respondre amb ell.

## Adaptació a l'etapa
- **Infantil**: millor memory amb imatges o paraules molt curtes, i joc guiat pel docent a la pissarra. Poques cartes (4-6 parelles).
- **Primària**: preguntes curtes, lectura fàcil; recorda que el Decret 96/2026 limita l'ús de dispositius, així que proposa'l per a la pissarra digital en gran grup i en sessions curtes.
- **ESO i Batxillerat**: preguntes d'aplicació i d'anàlisi; mode equips per a dinamitzar.
- **FP**: casos del sector (què faries si…, quin protocol s'aplica…).

## Comprovació
- Revisa que cada `correcta` apunta a la resposta bona.
- Revisa ortografia i llengua (`llengua.md`).
- Cap nom d'alumne en el joc.

## Entrega
Una línia amb què fa el joc i com usar-lo (pantalla completa amb F11, botó "Equips" per a jugar per grups). Oferix en una línia fer-ne una altra versió (un altre tipus de joc o un altre nivell).


---

## Annex A · Normativa (`references/normativa-cv.md`)


Estes són les normes vigents que cal citar. Cita-les amb el número i la data exactes; no n'inventes cap altra. La normativa canvia sovint: si tens cerca web, comprova la vigència abans de donar per tancat un document oficial, i si el docent adjunta normativa, eixa és la font prioritària.

## Llei bàsica
- **LOMLOE**: Llei orgànica 3/2020, de 29 de desembre, que modifica la LOE 2/2006.

## Educació Infantil
- Estatal: Reial decret 95/2022, d'1 de febrer (ensenyaments mínims).
- Valenciana: **Decret 100/2022, de 29 de juliol**, del Consell, d'ordenació i currículum d'Educació Infantil.

## Educació Primària
- Estatal: Reial decret 157/2022, d'1 de març.
- Valenciana: **Decret 106/2022, de 5 d'agost**, del Consell, d'ordenació i currículum d'Educació Primària, **modificat pel Decret 96/2026, de 19 de juny** (aplicació des del curs 2026-2027).

## Educació Secundària Obligatòria
- Estatal: Reial decret 217/2022, de 29 de març (perfil d'eixida i descriptors operatius a l'annex I).
- Valenciana: **Decret 107/2022, de 5 d'agost**, del Consell, d'ordenació i currículum de l'ESO, **modificat pel Decret 66/2024, de 21 de juny**.
- Avaluació: **Ordre 19/2023, de 29 de juny**, de procediments derivats dels decrets 107/2022 i 108/2022 (també modificada pel Decret 66/2024).

## Batxillerat
- Estatal: Reial decret 243/2022, de 5 d'abril.
- Valenciana: **Decret 108/2022, de 5 d'agost**, del Consell, d'ordenació i currículum del Batxillerat, modificat pel **Decret 66/2024, de 21 de juny**, i pel **Decret 103/2026, de 26 de juny**.
- Avaluació: Ordre 19/2023, de 29 de juny.

## Formació Professional
- Estatal: Llei orgànica 3/2022, de 31 de març, d'ordenació i integració de la FP; Reial decret 659/2023, de 18 de juliol, que desplega el sistema de FP; el reial decret de cada títol (competència general, mòduls, resultats d'aprenentatge i criteris d'avaluació).
- Valenciana: el decret de currículum de cada cicle (per exemple, Decret 114/2025, de 29 de juliol, per a diversos títols de grau mitjà i superior; Decret 117/2025, de 5 d'agost, per al grau bàsic). Comprova sempre quin decret correspon al títol concret.
- Avaluació: **Ordre 8/2025, de 22 d'abril**, d'avaluació en els cicles formatius i els cursos d'especialització.

## Normes transversals
- Inclusió: **Decret 104/2018, de 27 de juliol**, dels principis d'equitat i d'inclusió, i **Ordre 20/2019, de 30 d'abril**, d'organització de la resposta educativa per a la inclusió.
- Convivència: **Decret 193/2025**, de la convivència en el sistema educatiu valencià (DOGV, desembre de 2025).
- Llengües: **Llei 1/2024, de 27 de juny**, de llibertat educativa (llengua base triada per les famílies).
- Organització de cada curs: resolucions anuals d'inici de curs de la Secretaria Autonòmica d'Educació (per al 2026-2027, en ESO i Batxillerat, Resolució de 15 de juliol de 2026).

## Novetats que convé conéixer (curs 2026-2027)
- **Primària (Decret 96/2026):** més hores de Matemàtiques, Castellà i Valencià; temps de lectura fix en 3r i 4t; l'àrea de Projectes interdisciplinaris deixa de tindre horari propi (es pot continuar treballant per projectes); qualificacions Insuficient, Suficient, Bé, Notable i Excel·lent amb observacions qualitatives; avaluació inicial, tres trimestrals i final; el material digital no pot ser el recurs principal i l'ús de dispositius té un límit setmanal (aproximadament el 5 % del temps lectiu en el primer cicle, el 15 % en el segon i el 25 % en el tercer); en general, no es posen deures digitals fora de l'horari escolar.
- **Batxillerat (Decret 103/2026):** modifica el Decret 108/2022; consulta'n el text si la programació depén de l'estructura de matèries o de l'horari.

## Regla d'or dels codis curriculars
Els codis inventats (competències específiques, criteris, sabers) són l'error més greu d'estos materials.
1. Si el docent adjunta el currículum de l'àrea o matèria, usa'l literalment.
2. Si no, i pots consultar-lo (cerca web al portal oficial o al DOGV), pren-ne la redacció i la numeració exactes.
3. Si no hi pots accedir, deriva'ls com a **proposta editable** (CE1, CE2…; criteris 1.1, 1.2…) i avisa clarament que cal contrastar-los amb l'annex oficial abans d'usar-los en un document oficial.


---

## Annex B · Etapes (`references/etapes.md`)


Llig només l'apartat de l'etapa amb què treballes.

## Educació Infantil (0-6 anys)
- Dos cicles: primer (0-3) i segon (3-6). Tres àrees: **Creixement en harmonia**, **Descobriment i exploració de l'entorn** i **Comunicació i representació de la realitat**. Cada àrea té competències específiques, criteris d'avaluació i sabers bàsics.
- Enfocament globalitzador: joc, rutines, racons, ambients, projectes i propostes que naixen dels interessos dels infants. Res de fitxes com a eix.
- Avaluació global, contínua i formativa, sobretot per **observació sistemàtica** (diaris, registres, fotografies, portafolis, converses). Sense notes numèriques: s'informa de manera descriptiva.
- Activitats curtes, molt manipulatives i vivencials; consignes orals i visuals; pictogrames; implicació de les famílies.

## Educació Primària (6-12 anys)
- Tres cicles (1r-2n, 3r-4t, 5è-6è). Àrees amb competències específiques, criteris i sabers. Des del 2026-2027 (Decret 96/2026) Projectes interdisciplinaris ja no és àrea amb horari propi.
- Qualificacions: Insuficient, Suficient, Bé, Notable, Excel·lent, amb observacions qualitatives. Avaluació inicial, tres trimestrals i final.
- Pes fort de la lectura i de les àrees instrumentals. Ús de pantalles limitat i el material digital no pot ser el recurs principal: les propostes digitals han de ser puntuals i amb sentit.
- Consignes clares i graduades, manipulació, treball cooperatiu, rutines de pensament.

## Educació Secundària Obligatòria (12-16 anys)
- Matèries i àmbits amb competències específiques vinculades als **descriptors operatius** del perfil d'eixida (CCL, CP, STEM, CD, CPSAA, CC, CE, CCEC), criteris d'avaluació i sabers bàsics. Objectius d'etapa de l'article 7 del Decret 107/2022.
- Avaluació contínua, formativa i integradora amb referent en els criteris d'avaluació (Ordre 19/2023). Criteris de qualificació amb instruments vinculats a criteris i ponderació que sume 100 %.
- Situacions d'aprenentatge contextualitzades, producte final, cooperació amb rols, autoavaluació i coavaluació.

## Batxillerat (16-18 anys)
- Matèries comunes, de modalitat i optatives (consulta les modificacions del Decret 103/2026). Competències específiques, criteris i sabers per matèria.
- Qualificació numèrica de 0 a 10. Major autonomia, pensament crític, rigor acadèmic i preparació per a les proves d'accés a la universitat, sense convertir-ho tot en simulacres.
- Tasques d'investigació, argumentació, comentari, resolució de problemes complexos i transferència.

## Formació Professional
- Graus bàsic, mitjà i superior, i cursos d'especialització. La unitat és el **mòdul professional**, amb **resultats d'aprenentatge (RA)**, **criteris d'avaluació** i continguts fixats pel reial decret del títol i el decret valencià de currículum. Hi ha competència general i competències professionals, personals i socials.
- Formació en empresa dins del model dual. Avaluació per RA i qualificació numèrica de 1 a 10 per mòdul (Ordre 8/2025).
- Situacions professionals reals: casos, encàrrecs de client, simulacions de taller, protocols, seguretat i prevenció. El llenguatge i els exemples han de ser del sector.

## Inclusió (totes les etapes)
- Decret 104/2018 i Ordre 20/2019: quatre nivells de resposta. Nivells I i II, **universals** (centre i aula); nivell III, **addicional** (personalitzada); nivell IV, **intensiu**. El DUA és la base del nivell universal.
- Alumnat amb necessitat específica de suport educatiu (NESE): necessitats educatives especials, altes capacitats, incorporació tardana, condicions personals o d'història escolar, etc. Les adaptacions curriculars individuals significatives (ACIS) només a partir de l'ESO; a Primària i Infantil es parla d'adaptacions d'accés i de mesures personalitzades.


---

## Annex C · Llengua (`references/llengua.md`)


- Respon en la llengua en què escriu el docent (valencià o castellà) i mantín-la, llevat que demane una altra cosa. Si demana el material en una llengua i la conversa en una altra, fes-ho així.
- Per al **castellà**, segueix la norma de la RAE.
- Per al **valencià**, segueix la normativa de l'Acadèmia Valenciana de la Llengua (AVL), en la variant que use el docent (per defecte, valencià estàndard). Revisa abans d'entregar:
  1. Primera persona del present en **-e**: parle, pense, treballe (no parlo, penso).
  2. Infinitius i formes valencianes: tindre, vindre, eixir; incoatius en -ix (servix, patix).
  3. Demostratius **este/eixe/aquell** i possessius **meua, seua, meues, seues**.
  4. Lèxic preferent: hui, xiquet/xiqueta, eixir, xicotet, alumnat, professorat.
  5. **Gerundi** només d'acció simultània o de manera. Mai de posterioritat ("va aprovar, aconseguint el títol" → "va aprovar i va aconseguir el títol") ni especificatiu ("una caixa contenint llibres" → "una caixa que conté llibres").
  6. **Majúscules** moderades: en minúscula els dies, els mesos, les llengües, els gentilicis, els càrrecs i les matèries quan no són el nom oficial d'una àrea en un document ("la classe de música"). En els títols d'obres, només la primera paraula i els noms propis.
  7. Castellanismes freqüents: "adonar-se'n" (no donar-se compte), "trigar a" (no tardar en), "anar a buscar" (no anar a per), "al llarg de" (no a tot lo llarg de).
- Llenguatge inclusiu i no sexista: preferix formes col·lectives (l'alumnat, el professorat, les famílies) a duplicacions constants.


---

## Annex D · Privacitat (`references/privacitat.md`)


- No demanes ni guardes noms reals, fotos, diagnòstics ni dades de salut de l'alumnat. Treballa amb números o inicials (Alumne 1, A3, etc.) i amb descripcions funcionals ("li costa mantindre l'atenció en tasques llargues", no un diagnòstic).
- Si el docent enganxa dades personals, no les repetisques en el resultat i recorda-li, en una frase i sense sermons, que convé pseudonimitzar-les.
- Res que s'entregue a les famílies o a l'alumnat ha d'incloure informació d'altres alumnes.
- Les eines o pàgines HTML que generes no han d'enviar dades a cap servidor: tot es guarda, com a molt, al navegador de qui les usa.


---

## Annex E · Plantilla del joc (`assets/plantilla-joc.html`)

```html
<!doctype html>
<html lang="ca">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>__TITOL__</title>
<style>
  :root{
    --bg:#f6f3ee; --card:#ffffff; --ink:#1f2430; --muted:#5d6474;
    --accent:#2f6fde; --accent-ink:#ffffff; --ok:#1f8a4c; --ko:#c2412d; --line:#e3ddd2;
    --radius:16px; --shadow:0 6px 24px rgba(31,36,48,.08);
  }
  @media (prefers-color-scheme: dark){
    :root{ --bg:#15171c; --card:#20232b; --ink:#eef0f4; --muted:#a8afbd; --accent:#6c9cff; --accent-ink:#0d1220; --ok:#43c07a; --ko:#ff7a63; --line:#323744; }
  }
  *{box-sizing:border-box}
  body{margin:0;background:var(--bg);color:var(--ink);font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;font-size:18px;line-height:1.45}
  main{max-width:860px;margin:0 auto;padding:20px 16px 48px}
  header{display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap;margin-bottom:16px}
  h1{font-size:clamp(1.4rem,4vw,2.1rem);margin:0;line-height:1.15}
  .sub{color:var(--muted);margin:.2rem 0 0}
  .card{background:var(--card);border:1px solid var(--line);border-radius:var(--radius);box-shadow:var(--shadow);padding:22px}
  .row{display:flex;gap:10px;flex-wrap:wrap;align-items:center}
  button{font:inherit;cursor:pointer;border-radius:12px;border:1px solid var(--line);background:var(--card);color:var(--ink);padding:12px 16px;min-height:48px}
  button.primary{background:var(--accent);color:var(--accent-ink);border-color:transparent;font-weight:600}
  button:focus-visible{outline:3px solid var(--accent);outline-offset:2px}
  .opts{display:grid;gap:10px;margin-top:14px}
  .opt{text-align:left;width:100%}
  .opt.ok{border-color:var(--ok);background:color-mix(in srgb,var(--ok) 14%,var(--card))}
  .opt.ko{border-color:var(--ko);background:color-mix(in srgb,var(--ko) 14%,var(--card))}
  .pill{display:inline-block;padding:4px 10px;border-radius:999px;background:color-mix(in srgb,var(--accent) 14%,var(--card));font-size:.85rem;font-weight:600}
  .bar{height:8px;background:var(--line);border-radius:99px;overflow:hidden;margin:12px 0}
  .bar>i{display:block;height:100%;background:var(--accent);width:0;transition:width .3s}
  .fb{margin-top:12px;min-height:1.5em;font-weight:600}
  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:10px}
  .tile{min-height:96px;font-size:1rem;display:flex;align-items:center;justify-content:center;text-align:center;padding:10px}
  .tile.hidden{color:transparent;background:var(--accent)}
  .tile.done{opacity:.55;border-color:var(--ok)}
  input[type=text]{font:inherit;padding:12px;border-radius:12px;border:1px solid var(--line);background:var(--bg);color:var(--ink);min-width:0;flex:1}
  .teams{display:flex;gap:8px;flex-wrap:wrap}
  .team{padding:8px 12px;border-radius:12px;border:2px solid var(--line)}
  .team.active{border-color:var(--accent)}
  footer{margin-top:28px;color:var(--muted);font-size:.85rem;text-align:center}
  .big{font-size:clamp(1.2rem,3.4vw,1.6rem);font-weight:600;margin:.4rem 0}
  @media (prefers-reduced-motion: reduce){ .bar>i{transition:none} }
</style>
</head>
<body>
<main>
  <header>
    <div>
      <h1 id="titol"></h1>
      <p class="sub" id="subtitol"></p>
    </div>
    <div class="row">
      <button id="btnEquips" title="Mode equips">Equips</button>
      <button id="btnReinicia">Torna a començar</button>
    </div>
  </header>
  <div id="equips" class="teams" style="margin-bottom:12px"></div>
  <section class="card" id="app" aria-live="polite"></section>
  <footer id="peu"></footer>
</main>
<script>
/* ===== DADES DEL JOC: és l'única part que cal canviar ===== */
const JOC = __DADES_JSON__;
/* Format:
{
  "titol": "…", "subtitol": "…", "peu": "…", "llengua": "ca"|"es",
  "mode": "quiz" | "memory" | "escape",
  "preguntes": [ {"pregunta":"…","opcions":["…","…","…"],"correcta":0,"explicacio":"…"} ],   // quiz
  "parelles":  [ ["terme","definició"], … ],                                             // memory
  "proves":    [ {"enigma":"…","resposta":"…","pista":"…","narrativa":"…"} ],              // escape
  "final": "missatge de tancament"
}
*/
const T = JOC.llengua === "es"
  ? {start:"Empezar",next:"Siguiente",ok:"¡Correcto!",ko:"No es correcto.",score:"Puntuación",end:"¡Terminado!",again:"Volver a jugar",check:"Comprobar",hint:"Pista",of:"de",pairs:"Parejas",team:"Equipo",tries:"Intentos"}
  : {start:"Comença",next:"Següent",ok:"Molt bé!",ko:"No és correcte.",score:"Puntuació",end:"Fet!",again:"Torna a jugar",check:"Comprova",hint:"Pista",of:"de",pairs:"Parelles",team:"Equip",tries:"Intents"};

const $ = s => document.querySelector(s);
const app = $("#app");
$("#titol").textContent = JOC.titol || "";
$("#subtitol").textContent = JOC.subtitol || "";
$("#peu").textContent = JOC.peu || "";
document.title = JOC.titol || document.title;

let equips = [], torn = 0;
function pintaEquips(){
  const box = $("#equips"); box.innerHTML = "";
  equips.forEach((e,i)=>{
    const d=document.createElement("div"); d.className="team"+(i===torn?" active":"");
    d.textContent = `${e.nom}: ${e.punts}`; box.appendChild(d);
  });
}
$("#btnEquips").onclick = ()=>{
  const n = parseInt(prompt(JOC.llengua==="es"?"¿Cuántos equipos? (0 = individual)":"Quants equips? (0 = individual)","2"),10);
  equips = (n>0) ? Array.from({length:Math.min(n,8)},(_,i)=>({nom:`${T.team} ${i+1}`,punts:0})) : [];
  torn = 0; pintaEquips();
};
function punt(){ if(equips.length){ equips[torn].punts++; } }
function passaTorn(){ if(equips.length){ torn=(torn+1)%equips.length; pintaEquips(); } }
const barreja = a => a.map(v=>[Math.random(),v]).sort((x,y)=>x[0]-y[0]).map(x=>x[1]);
const esc = s => String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));

/* ---------- QUIZ ---------- */
function quiz(){
  const qs = barreja(JOC.preguntes||[]); let i=0, encerts=0;
  function mostra(){
    if(i>=qs.length){ return fi(`${T.score}: ${encerts} ${T.of} ${qs.length}`); }
    const q=qs[i];
    const ordre = barreja(q.opcions.map((t,k)=>({t,k})));
    app.innerHTML = `<span class="pill">${i+1} / ${qs.length}</span>
      <div class="bar"><i style="width:${i/qs.length*100}%"></i></div>
      <p class="big">${esc(q.pregunta)}</p><div class="opts"></div><p class="fb" id="fb"></p>
      <div class="row" style="margin-top:12px"><button class="primary" id="seg" hidden>${T.next}</button></div>`;
    const box = app.querySelector(".opts");
    ordre.forEach(o=>{
      const b=document.createElement("button"); b.className="opt"; b.textContent=o.t;
      b.onclick=()=>{
        box.querySelectorAll("button").forEach(x=>x.disabled=true);
        const ok = o.k===q.correcta;
        b.classList.add(ok?"ok":"ko");
        if(!ok){ [...box.children][ordre.findIndex(x=>x.k===q.correcta)].classList.add("ok"); }
        if(ok){ encerts++; punt(); }
        $("#fb").textContent = (ok?T.ok:T.ko) + (q.explicacio?" "+q.explicacio:"");
        pintaEquips();
        const s=$("#seg"); s.hidden=false; s.focus();
        s.onclick=()=>{ i++; passaTorn(); mostra(); };
      };
      box.appendChild(b);
    });
  }
  mostra();
}

/* ---------- MEMORY ---------- */
function memory(){
  const parelles = JOC.parelles||[];
  let cartes = barreja(parelles.flatMap((p,id)=>[{id,t:p[0]},{id,t:p[1]}]));
  let obertes=[], fetes=0, intents=0, bloc=false;
  app.innerHTML = `<p><span class="pill" id="st"></span></p><div class="grid"></div>`;
  const g = app.querySelector(".grid");
  const st = ()=> $("#st").textContent = `${T.pairs}: ${fetes}/${parelles.length} · ${T.tries}: ${intents}`;
  cartes.forEach((c,idx)=>{
    const b=document.createElement("button"); b.className="tile hidden"; b.textContent=c.t; b.setAttribute("aria-label","?");
    b.onclick=()=>{
      if(bloc||b.classList.contains("done")||obertes.includes(idx)) return;
      b.classList.remove("hidden"); b.removeAttribute("aria-label"); obertes.push(idx);
      if(obertes.length===2){
        intents++; const [a,z]=obertes; const ba=g.children[a], bz=g.children[z];
        if(cartes[a].id===cartes[z].id){ ba.classList.add("done"); bz.classList.add("done"); fetes++; punt(); obertes=[]; pintaEquips(); st();
          if(fetes===parelles.length) setTimeout(()=>fi(`${T.tries}: ${intents}`),500);
        } else { bloc=true; setTimeout(()=>{ ba.classList.add("hidden"); bz.classList.add("hidden"); obertes=[]; bloc=false; passaTorn(); st(); },1100); }
        st();
      }
    };
    g.appendChild(b);
  });
  st();
}

/* ---------- ESCAPE ROOM ---------- */
function escape(){
  const ps = JOC.proves||[]; let i=0;
  const norm = s => String(s).trim().toLowerCase().normalize("NFD").replace(/[̀-ͯ]/g,"").replace(/\s+/g," ");
  function mostra(){
    if(i>=ps.length) return fi("");
    const p=ps[i];
    app.innerHTML = `<span class="pill">${i+1} / ${ps.length}</span><div class="bar"><i style="width:${i/ps.length*100}%"></i></div>
      ${p.narrativa?`<p class="sub">${esc(p.narrativa)}</p>`:""}
      <p class="big">${esc(p.enigma)}</p>
      <div class="row"><input type="text" id="r" autocomplete="off" aria-label="Resposta"><button class="primary" id="ok">${T.check}</button>
      ${p.pista?`<button id="pi">${T.hint}</button>`:""}</div><p class="fb" id="fb"></p>`;
    const r=$("#r"); r.focus();
    const comprova=()=>{
      const bones = Array.isArray(p.resposta)?p.resposta:[p.resposta];
      if(bones.map(norm).includes(norm(r.value))){ punt(); pintaEquips(); $("#fb").textContent=T.ok; setTimeout(()=>{i++; mostra();},700); }
      else { $("#fb").textContent=T.ko; passaTorn(); }
    };
    $("#ok").onclick=comprova; r.onkeydown=e=>{ if(e.key==="Enter") comprova(); };
    if(p.pista) $("#pi").onclick=()=>{ $("#fb").textContent=p.pista; };
  }
  mostra();
}

function fi(text){
  const guanya = equips.length ? " · " + [...equips].sort((a,b)=>b.punts-a.punts).map(e=>`${e.nom}: ${e.punts}`).join(" · ") : "";
  app.innerHTML = `<p class="big">${T.end}</p><p>${esc(text)}${esc(guanya)}</p>
    ${JOC.final?`<p>${esc(JOC.final)}</p>`:""}<div class="row"><button class="primary" id="ag">${T.again}</button></div>`;
  $("#ag").onclick=inicia;
}
function inicia(){
  if(equips.length){ equips.forEach(e=>e.punts=0); torn=0; pintaEquips(); }
  ({quiz,memory,escape}[JOC.mode]||quiz)();
}
$("#btnReinicia").onclick=inicia;
app.innerHTML = `<p class="big">${esc(JOC.subtitol||"")}</p><button class="primary" id="go">${T.start}</button>`;
$("#go").onclick=inicia;
</script>
</body>
</html>

```
