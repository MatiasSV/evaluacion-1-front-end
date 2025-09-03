# evaluacion-1-front-end
En este documento voy a explicar todas las modificaciones que apliqué al los archivos
index.html y css.html

En primer lugar, eliminé todos los estilos inline que estaban anidados en algunos elementos
del archivo y los añadí donde corresponde, en el documento css.

Le añadí alamentos al root como nuevos colores y una variable para que las tarjetas tengan un 
espaciado entre medio.
Así estaba antes

:root{
  --verde:#2e7d32;      /* primario */
  --verde-claro:#43a047;/* secundario */
  --tierra:#8d6e63;     /* acento */
  --gris:#f5f7f9;       /* fondo suave */
  --oscuro:#0f172a;     /* texto principal */
  --blanco:#ffffff;
} 

Y así está ahora:

:root{
  --verde:#2e7d32;      /* primario */
  --verde-claro:#43a047;/* secundario */
  --tierra:#8d6e63;     /* acento */
  --gris:#f5f7f9;       /* fondo suave */
  --oscuro:#0f172a;     /* texto principal */
  --blanco:#ffffff;
  --esmeralda: #1155448f;
  --esmeralda2: #97d8c2;
  --blanco2: #F5F5DC;
  --turquesa1: #25ac7f;
  --esmeralda3: #095539;
  --space-4: 20px; /* añadido: gap para grids */
}


Hice un cambio con los enlaces de la barran de navegación, los convertí en botones 
agregando la clase btn y luego creando otra clase que es btn--secondary 

Antes: 

 <nav>
        <ul>
          <li><a href="#beneficios">Beneficios</a></li>
          <li><a href="#testimonios">Testimonios</a></li>
          <li><a href="#contacto">Contacto</a></li>
        </ul>
  </nav>   

Después:
<nav>
        <ul>
          <li><a class="btn btn--secondary" href="#beneficios">Beneficios</a></li>
          <li><a class="btn btn--secondary" href="#testimonios">Testimonios</a></li>
          <li><a class="btn btn--secondary" href="#contacto">Contacto</a></li>
        </ul>
    </nav>


Le agregué un botón que dice "Registrate" a la tarjeta que estaba dentro del contenedor del aside,
agregué más contenedores dentro para poder distribuir bien el contenido y que no se desordenara

Antes:
<aside class="hero__card" aria-label="Destacado">
        <h2 style="margin:0 0 8px">Oferta de lanzamiento</h2>
        <p style="margin:0 0 14px">Regístrate y obtén un 20% de descuento en tu primera compra.</p>
        <ul style="margin:0; padding-left:18px">
          <li>Envío a todo Chile</li>
          <li>Pago seguro</li>
          <li>Soporte cercano</li>
        </ul>
      </aside>     
Después
<aside class="hero__card" aria-label="Destacado">
        <h2>Oferta de lanzamiento</h2>
        <p>Regístrate y obtén un 20% de descuento en tu primera compra.</p>
        <div class="card__inside">
          <div class="card__inside2">
            <ul>
              <li>Envío a todo Chile</li>
              <li>Pago seguro</li>
              <li>Soporte cercano</li>
            </ul>
          </div>
          <div class="card__inside2">
            <a class="btn btn--primary" href="#">Regístrate</a>
          </div>
        </div>
    </aside>
 
Clases card inside en CSS:

.card__inside{display: flex;}
.card__inside2{margin-left: 20px;}

Le agregué un fondo de pantalla al contenedor hero para que hubiera una imagen en el fondo de la sección:

Así quedó en el CSS:

.hero{ background:linear-gradient(180deg, rgba(67,160,71,.08), rgba(67,160,71,0)); 
padding:64px 0 40px; 
background-image: url(resources/monstera.avif); 
background-size: cover; 
background-repeat: no-repeat; 
background-position: center;}


Le añadí estilos aside a los botones de cada seccion y un hover a los botones de la 
barra de navegación. Quedarían así:

.btn--secondary:hover{ transform:translateY(-2px); background:#26744f}
.btn--primary:active{ transform:translateY(0); background-color: #1b4d20; box-shadow:0 3px 8px rgba(46,125,50,.2); }  
.btn--secondary:active{ transform:translateY(0);background-color: #0f172a; box-shadow:0 3px 8px rgba(46,125,50,.2); }
.btn:disabled, .btn:disabled:hover{ background:#a5d6a7; box-shadow:none; cursor:not-allowed; transform:translateY(0); }


En las tarjetas de los testimonios le agregué las imágenes correspondientes a las personas
que dieron sus testimonios. De esta manera lo hice:

Antes: 
       <section id="testimonios" class="testimonios">
      <h2 style="margin:18px 0 10px">Lo que dicen nuestros clientes</h2>
      <div class="grid" style="grid-template-columns:repeat(3,1fr)">
        <blockquote class="testi">“Excelente calidad.” <br><strong>— Fernanda</strong></blockquote>
        <blockquote class="testi">“Volveré a comprar.” <br><strong>— Ricardo</strong></blockquote>
        <blockquote class="testi">“Amé el empaque.” <br><strong>— Isa</strong></blockquote>
      </div>
    </section>

Despues:
   <section id="testimonios" class="testimonios">
      <h2>Lo que dicen nuestros clientes</h2>
      <div class="grid grid--3">
        <blockquote class="testi">
          <img src="resources/fernanda.avif" alt="Fernanda" class="img-test">
          “Excelente calidad.” <br><strong>— Fernanda</strong>
        </blockquote>
        <blockquote class="testi">
          <img src="resources/ricardo.avif" alt="Ricardo" class="img-test">
          “Volveré a comprar.” <br><strong>— Ricardo</strong>
        </blockquote>
        <blockquote class="testi">
          <img src="resources/isa.avif" alt="Isa" class="img-test">
          “Amé el empaque.” <br><strong>— Isa</strong>
        </blockquote>
      </div>
    </section>   

Así quedaría en CSS:
        .testimonios{ padding:20px 0 40px; }
.testi{ background:var(--blanco); border:1px solid #e6ebf0; border-radius:14px; padding:18px; font-size:.95rem; }
.testi strong{ color:var(--verde); }
.img-test{ width:60px; height:60px; border-radius:50%; object-fit:cover; margin-bottom:10px; max-width: 100%;}

    
Por último cambié el footer, promero le cambie de color al color tierra ya que sentía que iba más con
la temática de lo que quería comunicar la página y le agregué una sección entre medio de los
derechos reservados y las redes sociales, que contienen los links de 'politica y privacidad' y 'terminos y condiciones'

Antes: 

<footer>
    <div class="container footer__wrap">
      <small>© <span id="year"></span> EcoVida. Todos los derechos reservados.</small>
      <div class="social" aria-label="Redes sociales">
        <a href="#">Instagram</a>
        <a href="#">Facebook</a>
        <a href="#">LinkedIn</a>
      </div>
    </div>
  </footer>

Despues:
    <footer>
    <div class="container footer__wrap">
      <small>© <span id="year"></span> EcoVida. Todos los derechos reservados.</small>
      <div>
        <a href="#" class="links">Política de privacidad</a> |
        <a href="#" class="links">Términos de servicio</a>
      </div>
      <div class="social" aria-label="Redes sociales">
        <a href="#">Instagram</a>
        <a href="#">Facebook</a>
        <a href="#">LinkedIn</a>
      </div>
    </div>
  </footer>

CSS:

footer{ margin-top:40px; background:var(--tierra); color:#d9e1e8; }
.footer__wrap{ padding:24px 0; display:flex; align-items:center; justify-content:space-between; gap:12px; }
.social a{ color:#d9e1e8; opacity:.9; text-decoration:none; margin-right:12px; }
.social a:hover{ opacity:1; text-decoration:underline; text-underline-offset:3px; }
.links{ display:block; color:#d9e1e8; opacity:.9; text-decoration:none; margin-right:12px; }
.links:hover{ opacity:1; text-decoration:underline; text-underline-offset:3px; }
   
