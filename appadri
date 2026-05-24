<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="default" />
  <meta name="apple-mobile-web-app-title" content="Directorio" />
  <title>Directorio</title>

  <!-- ============================================================
    PASO 1 — CAMBIA EL NOMBRE DE LA APP
    Cambia "Directorio" en <title> y en apple-mobile-web-app-title
    por el nombre que quieras, ej: "Directorio Empresa"
  ============================================================ -->

  <style>
    @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=DM+Mono&display=swap');

    :root {
      --bg:        #F5F4F0;
      --surface:   #FFFFFF;
      --border:    #E2E0D8;
      --text:      #1A1A18;
      --muted:     #7A7870;
      --hint:      #B0AEA6;
      --accent:    #3D52A0;
      --accent-bg: #EEF0FA;
      --accent-t:  #2A3A78;
      --sec:       #A05A3D;
      --sec-bg:    #FAF0EE;
      --sec-t:     #78331A;
      --radius:    14px;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

    body { font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--text); min-height: 100vh; }

    /* ---- Header ---- */
    .header {
      background: var(--surface);
      border-bottom: 1px solid var(--border);
      padding: 1rem 1.25rem 0.75rem;
      position: sticky; top: 0; z-index: 10;
    }

    .header h1 { font-size: 22px; font-weight: 600; letter-spacing: -0.5px; margin-bottom: 0.75rem; }

    .search-wrap {
      display: flex; align-items: center;
      background: var(--bg); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 10px 14px; gap: 10px;
    }
    .search-wrap svg { flex-shrink: 0; color: var(--hint); }
    .search-wrap input {
      border: none; background: transparent; outline: none;
      font-family: inherit; font-size: 15px; color: var(--text); flex: 1;
    }
    .search-wrap input::placeholder { color: var(--hint); }

    #clear-btn { background: none; border: none; cursor: pointer; color: var(--hint); display: none; padding: 0; line-height: 1; }

    /* ---- Contador ---- */
    .count-bar { padding: 0.6rem 1.25rem; font-size: 12px; color: var(--hint); font-family: 'DM Mono', monospace; letter-spacing: 0.03em; }

    /* ---- Lista ---- */
    #list { padding: 0 1rem 6rem; }

    /* ---- Etiqueta de sección ---- */
    .section-label {
      display: flex; align-items: center; justify-content: space-between;
      padding: 0.5rem 0.25rem 0.4rem;
      font-size: 11px; font-weight: 600; letter-spacing: 0.07em;
      text-transform: uppercase; color: var(--hint);
      margin-top: 0.5rem;
    }
    .section-label:first-child { margin-top: 0; }

    /* ---- Botón colapsar "Otros" ---- */
    .toggle-otros {
      background: none; border: none; cursor: pointer;
      font-family: inherit; font-size: 11px; font-weight: 600;
      letter-spacing: 0.07em; text-transform: uppercase;
      color: var(--accent); display: flex; align-items: center; gap: 4px;
      padding: 0;
    }
    .toggle-otros svg { transition: transform 0.2s; }
    .toggle-otros.collapsed svg { transform: rotate(-90deg); }

    /* ---- Tarjeta de contacto ---- */
    .card {
      background: var(--surface); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 1rem 1.1rem; margin-bottom: 8px;
      cursor: pointer; display: flex; align-items: center; gap: 12px;
      transition: border-color 0.15s, transform 0.1s;
      -webkit-user-select: none;
    }
    .card:active { transform: scale(0.985); border-color: var(--accent); }
    .card.es-secundario:active { border-color: var(--sec); }

    .avatar {
      width: 42px; height: 42px; border-radius: 50%;
      background: var(--accent-bg); color: var(--accent-t);
      font-weight: 600; font-size: 13px; letter-spacing: 0.5px;
      display: flex; align-items: center; justify-content: center; flex-shrink: 0;
    }
    .avatar.sec { background: var(--sec-bg); color: var(--sec-t); }

    .card-info { flex: 1; min-width: 0; }
    .card-name { font-size: 15px; font-weight: 500; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
    .card-sub  { font-size: 13px; color: var(--muted); margin-top: 2px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

    .card-chevron { color: var(--border); flex-shrink: 0; }

    /* ---- Sin resultados ---- */
    .empty { text-align: center; padding: 3rem 1rem; color: var(--hint); }
    .empty svg { margin-bottom: 12px; }
    .empty p { font-size: 14px; }

    /* ---- Bloque "Otros" colapsable ---- */
    #bloque-otros { overflow: hidden; transition: max-height 0.3s ease; }

    /* ---- Vista detalle ---- */
    #detail { display: none; padding: 0 1rem 6rem; }

    .back-btn {
      display: inline-flex; align-items: center; gap: 6px;
      font-size: 14px; color: var(--accent); background: none; border: none;
      cursor: pointer; padding: 1rem 0.25rem; font-family: inherit; font-weight: 500;
    }

    .detail-card { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius); overflow: hidden; }

    .detail-top {
      padding: 1.5rem 1.25rem 1.25rem;
      display: flex; align-items: center; gap: 14px;
      border-bottom: 1px solid var(--border);
    }

    .detail-avatar {
      width: 54px; height: 54px; border-radius: 50%;
      background: var(--accent-bg); color: var(--accent-t);
      font-weight: 600; font-size: 18px;
      display: flex; align-items: center; justify-content: center; flex-shrink: 0;
    }
    .detail-avatar.sec { background: var(--sec-bg); color: var(--sec-t); }

    .detail-name { font-size: 19px; font-weight: 600; letter-spacing: -0.3px; }
    .detail-role { font-size: 13px; color: var(--muted); margin-top: 3px; }

    .detail-fields { padding: 0.25rem 0; }

    .field-row {
      display: flex; align-items: center; gap: 14px;
      padding: 0.85rem 1.25rem;
      border-bottom: 1px solid var(--border);
    }
    .field-row:last-child { border-bottom: none; }

    .field-icon { color: var(--muted); flex-shrink: 0; }
    .field-text { flex: 1; min-width: 0; }
    .field-label { font-size: 11px; color: var(--hint); text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 2px; }
    .field-value { font-size: 14px; font-weight: 500; color: var(--text); word-break: break-word; }
  </style>
</head>
<body>

  <!-- ============================================================
    PASO 2 — TÍTULO VISIBLE EN LA APP
    Cambia el texto dentro de <h1>
  ============================================================ -->
  <div class="header">
    <h1>Directorio</h1>
    <div class="search-wrap">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <input type="search" id="search" placeholder="Buscar por nombre…" oninput="filtrar()" autocomplete="off" autocorrect="off" />
      <button id="clear-btn" onclick="limpiar()" aria-label="Borrar búsqueda">
        <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M18 6 6 18M6 6l12 12"/></svg>
      </button>
    </div>
  </div>

  <p class="count-bar" id="count"></p>
  <div id="list"></div>

  <div id="detail">
    <button class="back-btn" onclick="verLista()">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M15 18l-6-6 6-6"/></svg>
      Regresar
    </button>
    <div class="detail-card">
      <div class="detail-top">
        <div class="detail-avatar" id="d-avatar"></div>
        <div>
          <div class="detail-name" id="d-name"></div>
          <div class="detail-role" id="d-role"></div>
        </div>
      </div>
      <div class="detail-fields" id="d-fields"></div>
    </div>
  </div>


  <script>
  // ================================================================
  //  PASO 3A — CONTACTOS PRINCIPALES (acceso directo, siempre visibles)
  //
  //  Pon aquí tus 10 contactos más importantes.
  //  Campos disponibles (todos opcionales excepto "nombre"):
  //    nombre, rol, tel, dir, correo, nota
  //
  //  Reglas:
  //  · Cada contacto va entre { } separado por coma del siguiente
  //  · Los valores van entre comillas " "
  //  · Si un dato no aplica, pon "" y no aparecerá en el detalle
  //  · El ÚLTIMO contacto de la lista NO lleva coma al final
  // ================================================================

  const PRINCIPALES = [
    {
      nombre: "Ana García López",
      rol:    "Recursos Humanos",
      tel:    "444 123 4567",
      dir:    "Av. Venustiano Carranza 210, SLP",
      correo: "ana.garcia@empresa.com",
      nota:   "Horario: Lun–Vie 9–18 h"
    },
    {
      nombre: "Carlos Martínez Reyes",
      rol:    "Contabilidad",
      tel:    "444 987 6543",
      dir:    "Calle Independencia 55, SLP",
      correo: "cmartinez@empresa.com",
      nota:   ""
    },
    {
      nombre: "Diana Flores Herrera",
      rol:    "Ventas",
      tel:    "444 555 7890",
      dir:    "Blvd. Carranza 800, SLP",
      correo: "dflores@empresa.com",
      nota:   ""
    },
    {
      nombre: "Eduardo Ramírez Vega",
      rol:    "Sistemas",
      tel:    "444 321 0987",
      dir:    "Calle Zaragoza 33, SLP",
      correo: "eramirez@empresa.com",
      nota:   ""
    },
    {
      nombre: "Fernanda Torres Núñez",
      rol:    "Marketing",
      tel:    "444 654 3210",
      dir:    "Av. Universidad 1200, SLP",
      correo: "ftorres@empresa.com",
      nota:   ""
    },
    {
      nombre: "Gabriel Sánchez Mora",
      rol:    "Operaciones",
      tel:    "444 111 2233",
      dir:    "Privada Las Flores 7, SLP",
      correo: "gsanchez@empresa.com",
      nota:   ""
    },
    {
      nombre: "Ingrid López Castro",
      rol:    "Dirección",
      tel:    "444 445 6677",
      dir:    "Calle Allende 90, SLP",
      correo: "ilopez@empresa.com",
      nota:   ""
    },
    {
      nombre: "Jorge Mendoza Ríos",
      rol:    "Logística",
      tel:    "444 778 9900",
      dir:    "Calle Hidalgo 14, SLP",
      correo: "jmendoza@empresa.com",
      nota:   ""
    },
    {
      nombre: "Karen Villanueva Peña",
      rol:    "Legal",
      tel:    "444 334 5566",
      dir:    "Blvd. Antonio Rocha 500, SLP",
      correo: "kvillanueva@empresa.com",
      nota:   ""
    },
    {
      nombre: "Luis Herrera Guzmán",
      rol:    "Compras",
      tel:    "444 990 1122",
      dir:    "Av. Salvador Nava 300, SLP",
      correo: "lherrera@empresa.com",
      nota:   ""
    }
  ];


  // ================================================================
  //  PASO 3B — CONTACTOS SECUNDARIOS (colapsados por defecto)
  //
  //  Misma estructura que arriba. Aparecen bajo la sección "Otros",
  //  tapas una vez para expandirlos, otra vez para colapsarlos.
  // ================================================================

  const SECUNDARIOS = [
    {
      nombre: "María Estrada Campos",
      rol:    "Administración",
      tel:    "444 201 3344",
      dir:    "Calle Morelos 88, SLP",
      correo: "mestrada@empresa.com",
      nota:   ""
    },
    {
      nombre: "Nicolás Pedraza Luna",
      rol:    "Almacén",
      tel:    "444 202 4455",
      dir:    "Zona Industrial, SLP",
      correo: "npedraza@empresa.com",
      nota:   ""
    },
    {
      nombre: "Olivia Ramos Vidal",
      rol:    "Calidad",
      tel:    "444 203 5566",
      dir:    "Av. Industria 900, SLP",
      correo: "oramos@empresa.com",
      nota:   ""
    },
    {
      nombre: "Pablo Jiménez Soto",
      rol:    "Mantenimiento",
      tel:    "444 204 6677",
      dir:    "Calle Reforma 22, SLP",
      correo: "pjimenez@empresa.com",
      nota:   ""
    },
    {
      nombre: "Queenie Salazar Torres",
      rol:    "Recepción",
      tel:    "444 205 7788",
      dir:    "Av. Constitución 1, SLP",
      correo: "qsalazar@empresa.com",
      nota:   ""
    },
    {
      nombre: "Ricardo Aguilar Nava",
      rol:    "TI",
      tel:    "444 206 8899",
      dir:    "Calle Juárez 77, SLP",
      correo: "raguilar@empresa.com",
      nota:   ""
    },
    {
      nombre: "Sofía Delgado Ibarra",
      rol:    "Finanzas",
      tel:    "444 207 9900",
      dir:    "Blvd. Del Ejército 400, SLP",
      correo: "sdelgado@empresa.com",
      nota:   ""
    },
    {
      nombre: "Tomás Guerrero Ávila",
      rol:    "Producción",
      tel:    "444 208 0011",
      dir:    "Parque Industrial, SLP",
      correo: "tguerrero@empresa.com",
      nota:   ""
    },
    {
      nombre: "Úrsula Montes Paz",
      rol:    "Diseño",
      tel:    "444 209 1122",
      dir:    "Calle Pino Suárez 3, SLP",
      correo: "umontes@empresa.com",
      nota:   ""
    },
    {
      nombre: "Valentina Cruz Espino",
      rol:    "Proyectos",
      tel:    "444 210 2233",
      dir:    "Av. Tangamanga 150, SLP",
      correo: "vcruz@empresa.com",
      nota:   ""
    }
  ];


  // ================================================================
  //  PASO 4 — CAMPOS QUE SE MUESTRAN EN EL DETALLE
  //
  //  Para QUITAR un campo: borra toda esa línea { … }
  //  Para AGREGAR uno nuevo: copia una línea, cambia key y label
  //  El key debe coincidir EXACTAMENTE con el nombre en PRINCIPALES/SECUNDARIOS
  // ================================================================

  const CAMPOS = [
    {
      key: "tel", label: "Teléfono",
      icon: `<svg width="18" height="18" fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81 19.79 19.79 0 01.22 1.18 2 2 0 012.22 0h3a2 2 0 012 1.72c.13.96.36 1.9.7 2.81a2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0122 14.92z"/></svg>`
    },
    {
      key: "dir", label: "Dirección",
      icon: `<svg width="18" height="18" fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M21 10c0 7-9 13-9 13S3 17 3 10a9 9 0 1118 0z"/><circle cx="12" cy="10" r="3"/></svg>`
    },
    {
      key: "correo", label: "Correo",
      icon: `<svg width="18" height="18" fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="M2 7l10 7 10-7"/></svg>`
    },
    {
      key: "nota", label: "Nota",
      icon: `<svg width="18" height="18" fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>`
    },
  ];


  // ================================================================
  //  A PARTIR DE AQUÍ NO HAY QUE MODIFICAR NADA
  // ================================================================

  const TODOS = [
    ...PRINCIPALES.map(c => ({ ...c, _tipo: 'principal' })),
    ...SECUNDARIOS.map(c => ({ ...c, _tipo: 'secundario' }))
  ];

  let otrosAbiertos = false;
  let modoFiltro    = false;

  function iniciales(nombre) {
    return nombre.trim().split(/\s+/).slice(0, 2).map(p => p[0].toUpperCase()).join('');
  }

  function tarjeta(c, idx) {
    const esSec = c._tipo === 'secundario';
    const sub   = [c.rol, c.tel].filter(Boolean).join(' · ');
    return `
      <div class="card${esSec ? ' es-secundario' : ''}" onclick="verDetalle(${idx})">
        <div class="avatar${esSec ? ' sec' : ''}">${iniciales(c.nombre)}</div>
        <div class="card-info">
          <div class="card-name">${c.nombre}</div>
          ${sub ? `<div class="card-sub">${sub}</div>` : ''}
        </div>
        <div class="card-chevron">
          <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M9 18l6-6-6-6"/></svg>
        </div>
      </div>`;
  }

  function renderLista() {
    const lista = document.getElementById('list');
    const count = document.getElementById('count');
    const q     = document.getElementById('search').value.toLowerCase().trim();
    modoFiltro  = q.length > 0;

    if (modoFiltro) {
      const res = TODOS.map((c, i) => ({ c, i })).filter(({ c }) => c.nombre.toLowerCase().includes(q));
      count.textContent = `${res.length} resultado${res.length !== 1 ? 's' : ''} de ${TODOS.length}`;
      lista.innerHTML = res.length
        ? res.map(({ c, i }) => tarjeta(c, i)).join('')
        : `<div class="empty"><svg width="36" height="36" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg><p>Sin resultados</p></div>`;
      return;
    }

    count.textContent = `${TODOS.length} contactos`;

    const chevronDir = otrosAbiertos ? '0' : '-90';
    const labelOtros = otrosAbiertos ? 'Ocultar' : 'Mostrar';

    lista.innerHTML = `
      <div class="section-label">Principales</div>
      ${PRINCIPALES.map((c, i) => tarjeta(TODOS[i], i)).join('')}

      <div class="section-label">
        <span>Otros</span>
        <button class="toggle-otros${otrosAbiertos ? '' : ' collapsed'}" onclick="toggleOtros()" aria-label="Mostrar u ocultar otros contactos">
          ${labelOtros}
          <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24" style="transform:rotate(${chevronDir}deg);transition:transform 0.2s"><path d="M6 9l6 6 6-6"/></svg>
        </button>
      </div>

      <div id="bloque-otros" style="max-height:${otrosAbiertos ? '9999px' : '0px'}; overflow:hidden; transition: max-height 0.3s ease;">
        ${SECUNDARIOS.map((c, i) => tarjeta(TODOS[PRINCIPALES.length + i], PRINCIPALES.length + i)).join('')}
      </div>`;
  }

  function toggleOtros() {
    otrosAbiertos = !otrosAbiertos;
    renderLista();
  }

  function filtrar() {
    document.getElementById('clear-btn').style.display =
      document.getElementById('search').value ? 'block' : 'none';
    renderLista();
  }

  function limpiar() {
    document.getElementById('search').value = '';
    filtrar();
    document.getElementById('search').focus();
  }

  function verDetalle(idx) {
    const c   = TODOS[idx];
    const sec = c._tipo === 'secundario';

    const av = document.getElementById('d-avatar');
    av.textContent = iniciales(c.nombre);
    av.className   = 'detail-avatar' + (sec ? ' sec' : '');

    document.getElementById('d-name').textContent = c.nombre;
    document.getElementById('d-role').textContent = c.rol || '';

    const campos = CAMPOS
      .filter(f => c[f.key] && c[f.key].toString().trim() !== '')
      .map(f => `
        <div class="field-row">
          <div class="field-icon">${f.icon}</div>
          <div class="field-text">
            <div class="field-label">${f.label}</div>
            <div class="field-value">${c[f.key]}</div>
          </div>
        </div>`).join('');

    document.getElementById('d-fields').innerHTML = campos ||
      '<div class="field-row"><div class="field-text"><div class="field-value" style="color:var(--hint)">Sin campos adicionales</div></div></div>';

    document.getElementById('list').style.display    = 'none';
    document.getElementById('detail').style.display  = 'block';
    document.querySelector('.header').style.display  = 'none';
    document.getElementById('count').style.display   = 'none';
    window.scrollTo(0, 0);
  }

  function verLista() {
    document.getElementById('list').style.display    = 'block';
    document.getElementById('detail').style.display  = 'none';
    document.querySelector('.header').style.display  = 'block';
    document.getElementById('count').style.display   = 'block';
    window.scrollTo(0, 0);
  }

  renderLista();
  </script>
</body>
</html>
