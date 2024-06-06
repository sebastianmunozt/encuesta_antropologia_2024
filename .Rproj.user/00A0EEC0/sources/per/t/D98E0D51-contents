
# 1. Instalo y abro paquetes -------------------------------------------------
 install.packages("pacman")
pacman::p_load(tidyverse,# Universo de paquetes : tidyr, dplyr, ggplot2,readr,purrr,tibble, stringr, forcats
               openxlsx,#leer archivos xlsx
               readxl,# leer archivos xl      #dos formatos de excel xlsx y xl
               janitor,#limpieza de datos
               writexl,#Guardar tablas formato excel
               DataExplorer) #Exploración rápida

# 2. Importo archivo y lo asigno a environment ----------------------------
base_antropologia <- read.xlsx("Métodos Cuantitativos III (respuestas).xlsx")
libro_codigos<- read.xlsx("Métodos Cuantitativos III (respuestas).xlsx") # dejo una base sin limpiar para observar nombres de preguntas

#Explorar
glimpse(base_antropologia) #Una primera mirada de lo que hay en mis datos, la primera fila es extraña, dice "respuesta" o repite el nombre de la variable.
names(base_antropologia) #observo que hay puntos, mayúsculas y minúsculas, etcétera. Está sucia


# 3. Data Wrangling -------------------------------------------------------
#3.1. limpieza inicial
base_antropologia <- janitor::clean_names(base_antropologia) #con esto transformo todo a minúscula, quito tildes, saco signos, borro espacios
names(base_antropologia) # queda mucho mejor

#3.2. observación de base
nrow(base_antropologia) #147 cantidad de casos
ncol(base_antropologia) #50 cantidad de variables
sapply(base_antropologia, FUN = class) # sapply: realiza un a función a varias variables 
str(base_antropologia) #estructura del objeto base de datos

#3.3.Renombrar variables 
#extraigo el nombre de todas las variables
names (base_antropologia)

# Lista completa de nombres de variables
nombres_de_variables <- c(
  "marca_temporal",
  "direccion_de_correo_electronico",
  "cual_es_el_nombre_de_su_encuestadxr",
  "sd_01_usted_se_encuentra_cursando_la_carrera_de_antropologia",
  "sd_02_se_entiende_identidad_de_genero_como_la_vivencia_interna_e_individual_del_genero_tal_como_cada_persona_la_siente_profundamente_la_cual_podria_corresponder_o_no_con_el_sexo_asignado_al_momento_del_nacimiento_asi_por_un_lado_las_personas_cigenero_se_identifican_con_la_identidad_de_genero_que_les_asignaron_al_nacer_y_no_buscan_transitar_de_genero_y_por_otro_lado_las_personas_trans_no_se_identifican_con_la_identidad_de_genero_que_les_asignaron_al_nacer_y_por_lo_tanto_transitan_de_genero_para_manifestar_el_que_realmente_les_identifica_segun_estas_definiciones_cual_es_su_identidad_de_genero",
  "sd_03_que_edad_tiene",
  "sd_04_en_que_ano_ingreso_a_la_carrera",
  "sd_05_en_que_comuna_reside",
  "sd_06_en_la_sociedad_comunmente_existen_distintos_grupos_o_clases_sociales_las_personas_de_clase_social_alta_son_las_que_tienen_los_ingresos_mas_altos_el_mayor_nivel_de_educacion_y_los_trabajos_mas_valorados_las_personas_de_clase_social_baja_son_las_que_tienen_los_ingresos_mas_bajos_el_menor_nivel_de_educacion_y_los_trabajos_menos_valorados_entre_estas_clases_existen_otras_intermedias_segun_su_opinion_a_cual_de_los_siguientes_grupos_o_clases_sociales_pertenece_usted",
  "sd_07_indique_el_maximo_nivel_educativo_completado_obtenido_por_su_padre_o_figura_paterna",
  "sd_08_indique_el_maximo_nivel_educativo_completado_obtenido_por_su_madre_o_figura_materna",
  "sd_09_indique_el_ultimo_tipo_de_establecimiento_educativo_que_usted_asistio_al_realizar_su_ensenanza_media",
  "ea_01_cuantas_horas_dedica_aproximadamente_al_estudio_y_a_la_realizacion_de_trabajos_universitarios_fuera_del_aula_por_cada_dia_una_semana_habil_esto_es_de_lunes_a_viernes_por_ejemplo_si_lunes_y_martes_suelo_estudiar_mas_o_menos_3_horas_miercoles_5_horas_y_finalmente_jueves_y_viernes_suelo_estudiar_2_horas_el_total_de_horas_es_15_dividido_por_15_por_5_me_da_3_deberia_marcar_la_alternativa_b_3_o_4_horas",
  "ea_02_cuantas_horas_dedica_aproximadamente_al_estudio_cada_dia_a_lo_largo_del_fin_de_semana_sabado_y_domingo",
  "ea_03_como_describiria_su_carga_academica_actual",
  "ea_04_en_el_ultimo_semestre_finalizado_aproximadamente_que_promedio_de_notas_ha_obtenido_considere_el_ultimo_semestre_finalizado_como_el_segundo_semestre_del_ano_2023",
  "ea_05_que_tan_satisfecho_esta_con_tu_rendimiento_academico_en_el_ultimo_semestre_finalizado_considere_el_ultimo_semestre_finalizado_como_el_segundo_semestre_del_ano_2023",
  "ea_06_en_una_escala_del_1_al_5_donde_1_es_minimo_estres_y_5_es_maximo_estres_como_calificaria_su_nivel_de_estres_en_la_universidad_en_el_ultimo_semestre_finalizado",
  "ea_07_en_que_medidas_el_estres_afecta_su_rendimiento_academico",
  "ea_08_puede_identificar_por_si_mismo_cuando_se_siente_estresado_debidos_a_factores_relacionados_con_el_ambito_universitario",
  "ea_09_cuando_esta_en_periodos_de_evaluaciones_academicas_ha_tenido_alguno_de_estos_sintomas_seleccione_todas_las_alternativas_que_correspondan_con_su_caso",
  "ea_10_que_estrategias_utiliza_con_mayor_frecuencia_para_manejar_el_estres_academico_seleccione_todas_las_alternativas_que_correspondan_con_su_caso",
  "re_01_como_califica_su_creencia_de_un_ser_supremo_o_deidades",
  "re_02_cual_es_su_afiliacion_religiosa_o_creencia_espiritual_selecciona_una_opcion",
  "re_03_con_que_frecuencia_acude_a_su_religion_o_a_instancias_en_donde_conectes_con_tu_espiritualidad_rezo_oracion_meditacion_u_otro",
  "re_04_asiste_con_regularidad_a_algun_lugar_destinado_al_culto_religioso",
  "re_05_consideras_que_hay_una_influencia_de_la_religion_o_la_espiritualidad_en_sus_decisiones_eticas_y_morales_que_toma_en_su_vida_cotidiana",
  "rs_01_cuantas_horas_al_dia_pasa_en_redes_sociales_debes_considerar_la_suma_de_todas_las_redes_sociales_que_utilices",
  "rs_02_cuales_son_las_principales_razones_por_las_que_utiliza_redes_sociales_seleccione_todas_las_alternativas_que_correspondan_con_su_caso",
  "rs_03_experimenta_una_sensacion_de_necesidad_o_expectativa_social_de_mantener_una_presencia_activa_en_sus_redes_sociales_mediante_la_publicacion_de_fotos_videos_etcetera",
  "rs_04_como_gestiona_el_estres_relacionado_con_el_uso_de_redes_sociales",
  "rs_05_que_red_social_sueles_ocupar_con_mayor_frecuencia_seleccione_una_unica_respuesta",
  "rs_06_cual_es_la_segunda_red_social_que_sueles_ocupar_con_frecuencia",
  "to_01_cuanto_tiempo_libre_considera_que_ha_tenido_por_semana_para_dedicarse_a_actividades_fuera_del_ambito_universitario_considere_actividades_fuera_del_ambito_universitario_tales_como_deporte_entretenimiento_salidas_fiestas_etc",
  "to_02_considere_esta_definicion_de_ocio_antes_de_contestar_esta_y_las_siguientes_preguntas_el_ocio_se_puede_entender_como_el_tiempo_del_que_dispone_una_persona_para_distraerse_e_idealmente_disfrutar_de_un_momento_agradable_en_su_agenda_personal_o_tiempo_libre_tales_como_salir_tener_vida_social_hacer_deporte_o_practicas_de_consumo_o_participacion_cultural_leer_escuchar_o_tocar_musica_estar_en_internet_excluya_trabajo_y_estudio_ahora_que_ya_comprende_a_que_se_refiere_el_ocio_en_esta_encuesta_responda_cuantos_dias_a_la_semana_incluyendo_semana_y_fin_semana_realiza_actividades_de_ocio",
  "to_03_administra_su_tiempo_de_forma_optima_para_equilibrar_tus_obligaciones_academicas_con_las_actividades_de_ocio",
  "to_04_cuales_de_estas_actividades_prefiere_realizar_en_su_tiempo_de_ocio_seleccione_un_maximo_de_3_alternativas",
  "to_05_forma_parte_de_un_club_colectivo_o_taller_donde_se_realicen_actividades_las_actividades_previamente_mencionadas",
  "to_06_que_tan_importante_es_para_usted_el_tiempo_dedicado_a_actividades_de_ocio",
  "ma_01_en_una_escala_del_1_10_siendo_el_10_el_mayor_nivel_de_informacion_y_el_1_el_menor_que_tan_informado_se_encuentra_con_respecto_a_la_problematica_del_exceso_de_basura_en_las_calles",
  "ma_02_en_una_escala_del_1_al_10_que_tan_interesado_estaria_en_participar_en_actividades_educativas_que_amplien_su_conocimiento_sobre_gestion_de_residuos_y_problemas_relacionados",
  "ma_03_ha_participado_en_algun_grupo_organizacion_o_proyecto_ecologicos_relacionados_con_el_cuidado_y_preservacion_del_medio_ambiente",
  "ma_04_ha_participado_en_eventos_o_actividades_comunitarias_relacionadas_a_la_difusion_de_informacion_con_respecto_a_los_problemas_medioambientales_dentro_de_los_ultimos_tres_meses_meses_tales_como_charlas_ferias_ecologicas_talleres_practicos_o_campanas_especificas",
  "ma_05_con_que_frecuencia_adquiere_productos_sostenibles_o_amigables_con_el_medio_ambiente_teniendo_en_cuenta_la_reduccion_de_residuos_generados_por_sus_envases_ttales_como_botellas_reciclables_productos_a_granel_empaques_minimalistas_o_envases_reciclables",
  "cm_01_aproximadamente_con_que_frecuencia_suele_escuchar_musica_durante_la_semana_seleccione_una_unica_respuesta_considere_cada_numero_como_la_cantidad_de_dias_que_escucha_musica",
  "cm_02_aproximadamente_cuantas_horas_al_dia_escucha_musica_seleccione_una_unica_respuesta",
  "cm_03_que_genero_musical_suele_escuchar_con_frecuencia_seleccione_una_unica_respuesta",
  "cm_04_cual_es_el_segundo_genero_musical_que_suele_escuchar_con_frecuencia_seleccione_una_unica_respuesta",
  "cm_05_donde_suele_escuchar_musica_habitualmente_seleccione_mas_de_una_alternativa_si_corresponde",
  "cm_06_que_tan_importante_es_la_musica_para_ti_en_su_dia_a_dia_seleccione_una_unica_respuesta"
)

# Extraer las primeras cuatro letras de cada nombre de variable
primeras_5_letras <- substr(nombres_de_variables, 1, 5)

#primer argumento - string = de donde saco los nombres: el vector creado
#segundo argumento - start = desde que posición extraigo (p)
#tercer argumento - end= hasta donde (1)

#renombro considerando todas las columnas elegidas asignando nuevos nombres
base_antropologia <- base_antropologia %>%
  rename_at(vars(nombres_de_variables), ~ primeras_5_letras) #recodificación múltiples con un vector

names(base_antropologia)

#renombro algunas variables en específico
names(base_antropologia)

#posibilidad de renombrar uno por uno las variables de interés. # primero nuevo nombre y luego nombre antiguo
#estructura: base_datos <- base_datos %>% dplyr::rename(nombrenuevo=nombre_antiguo,nombre_nuevo=nombre_antiguo)

base_antropologia <- base_antropologia %>% dplyr::rename (n_encuestador = cual_)
names(base_antropologia)


# Trabajo con variables sociodemográficas
# Limpieza de variable: n_encuestador: realizada por SAMANTA.
# Por ser una pregunta abierta hago una limpieza de categorías
# Elimino caracteres latinos, las pongo todas en minúsculas, reemplazo espacios por guión bajo.

base_antropologia <- base_antropologia %>%
  mutate(
    n_encuestador = stringi::stri_trans_general(n_encuestador, "Latin-ASCII"),  # Convierte caracteres latinos en la columna `n_encuestador` a su equivalente ASCII
    n_encuestador = tolower(n_encuestador),  # Convierte todos los caracteres en la columna `n_encuestador` a minúsculas
    n_encuestador = gsub(" ", "_", n_encuestador),  # Reemplaza espacios por guiones bajos en la columna `n_encuestador`
  )

unique(base_antropologia$n_encuestador) #observo mucha variedad de como se escriben los nombres. 

# voy a recodificar los nombres, para ello hago lo siguiente
# hago un listado de los nombres 
valores_unicos_a<- sort(unique(base_antropologia$n_encuestador), decreasing = F)

#imprimo los valores ordenados, para verlos, copiarlos y recodificarlos. 
print(valores_unicos_descendentes)

#hago un proceso de recodificación: por ejemplo con Alejandra Mondaca, Alonso silva y Amanda Baez (SEGUIR!)
base_antropologia <- base_antropologia %>%
  mutate(n_encuestador=case_when(n_encuestador== "alejandra_"~ "Alejandra Mondaca",
                                 n_encuestador=="alejandra_mondaca" ~ "Alejandra Mondaca",
                                 n_encuestador=="alejandra_mondaca_" ~ "Alejandra Mondaca",
                                 n_encuestador=="alonso_silva" ~ "Alonso Silva",
                                 n_encuestador=="alonso_silva_" ~ "Alonso Silva",
                                 n_encuestador=="amanda_baez" ~ "Amanda Baez",
                                 n_encuestador=="amanda_baez_" ~ "Amanda Baez",
                                 TRUE ~n_encuestador))

base_antropologia <- base_antropologia %>%
  mutate(n_encuestador=case_when(n_encuestador=="carla_(buffy)" ~ "Alejandra Mondaca",
                                 n_encuestador=="alexi" ~ "Alejandra Mondaca",
                                 n_encuestador=="alejandra_mondaca" ~ "Alejandra Mondaca",
                                 n_encuestador=="alejandra_mondaca_" ~ "Alejandra Mondaca",
                                 n_encuestador=="alonso_silva" ~ "Alonso Silva", 
                                 n_encuestador=="alonso_silva_" ~ "Alonso Silva",
                                 n_encuestador=="amanda_baez" ~ "Amanda Baez",
                                 n_encuestador=="amanda_baez_" ~ "Amanda Baez",
                                 n_encuestador=="antonia_ramirez_" ~ "Antonia Ramirez",
                                 n_encuestador=="camila_crisostomo" ~ "Camila Crisostomo",
                                 n_encuestador=="camila_segura" ~ "Camila Segura",
                                 n_encuestador=="catalina_" ~ "Catalina Fuentes",
                                 n_encuestador=="catalina_fuentes" ~ "Catalina Fuentes",
                                 n_encuestador=="consuelo_llanten_" ~ "Consuelo Llanten",
                                 n_encuestador=="consuelo_llanten" ~ "Consuelo Llanten",
                                 n_encuestador=="alejandra_"~ "Daniela Pasmino",
                                 n_encuestador=="daniela_berrios" ~ "Daniela Pasmino",
                                 n_encuestador=="daniela_pasmino" ~ "Daniela Pasmino",
                                 n_encuestador=="florencia_martin" ~"Florencia Martin",
                                 n_encuestador=="florencia_martin_" ~ "Florencia Martin",
                                 n_encuestador=="gabriel_concha" ~ "Gabriel Concha",
                                 n_encuestador=="gabriel_concha_" ~ "Gabriel Concha",
                                 n_encuestador=="gonzalo" ~ "Gonzalo Munoz",
                                 n_encuestador=="gonzalo_" ~ "Gonzalo Munoz",
                                 n_encuestador=="gonzalo_munoz" ~ "Gonzalo Munoz",
                                 n_encuestador=="gonzalo_munoz_oliva_" ~ "Gonzalo Munoz",
                                 n_encuestador=="isidora_aros" ~ "Isidora Aros",
                                 n_encuestador=="isidora_aros_" ~ "Isidora Aros",
                                 n_encuestador=="joaquin" ~ "Joaquin Castillo",
                                 n_encuestador=="joaquin_" ~ "Joaquin Castillo",
                                 n_encuestador=="joaquin_castillo" ~ "Joaquin Castillo",
                                 n_encuestador=="yakim_" ~ "Joaquin Castillo",
                                 n_encuestador=="javiera_herrera" ~ "Javiera Herrera",
                                 n_encuestador=="joaquin_orellana_" ~ "Joaquin Orellana",
                                 n_encuestador=="juan" ~ "Joaquin Orellana",
                                 n_encuestador=="julia_sotomayor"~ "Julia Sotomayor",
                                 n_encuestador=="elisa_monsalve_"~ "Julia Sotomayor",
                                 n_encuestador=="escarleth_"~ "Julia Sotomayor",
                                 n_encuestador=="franco" ~ "Julia Sotomayor",
                                 n_encuestador== "krishna_asencio" ~ "Krishna Asencio", 
                                 n_encuestador== "krishna_asencio_" ~ "Krishna Asencio", 
                                 n_encuestador=="antonia_leiva" ~ "Mariana Perez",
                                 n_encuestador=="mariana_perez" ~ "Mariana Perez",
                                 n_encuestador=="mariana_perez_" ~ "Mariana Perez",
                                 n_encuestador== "pablo_cornejo" ~ "Mariana Perez", 
                                 n_encuestador== "martin_campusano" ~ "Martin Campusano", 
                                 n_encuestador== "martin_cifuentes" ~ "Martin Cifuentes", 
                                 n_encuestador== "matilde_cespedes" ~ "Matilde Cespedes", 
                                 n_encuestador== "matilde_cespedes_" ~ "Matilde Cespedes", 
                                 n_encuestador== "antonia_" ~ "Noel Casas-Cordero",
                                 n_encuestador== "noel_casas-cordero"~ "Noel Casas-Cordero",
                                 n_encuestador== "oliver_delherbe" ~ "Oliver Delherbe", 
                                 n_encuestador== "olivier_delherbe" ~ "Oliver Delherbe", 
                                 n_encuestador== "patricia_gonzalez" ~ "Patricia Gonzalez", 
                                 n_encuestador== "patricia_gonzalez_" ~ "Patricia Gonzalez", 
                                 n_encuestador== "pedro_villaroel" ~ "Pedro Villaroel", 
                                 n_encuestador== "pedro_villarroel" ~ "Pedro Villaroel", 
                                 n_encuestador== "martina_" ~ "Pedro Villaroel", 
                                 n_encuestador== "samanta_letelier" ~ "Samanta Letelier", 
                                 n_encuestador== "samanta_letelier_" ~ "Samanta Letelier", 
                                 n_encuestador== "sofia_ballerino" ~ "Sofia Ballerino", 
                                 n_encuestador== "sofia_ballerino_" ~ "Sofia Ballerino",
                                 n_encuestador== "valentina" ~ "Valentina Gonzalez",
                                 n_encuestador== "valentina_gonzalez" ~ "Valentina Gonzalez",
                                 n_encuestador== "valentina_gonzalez_" ~ "Valentina Gonzalez",
                                 n_encuestador== "valeria_carvajal" ~ "Valeria Carvajal",
                                 n_encuestador== "valeria_carvajal_donoso" ~ "Valeria Carvajal",
                                 n_encuestador== "valeria_carvajal_" ~ "Valeria Carvajal",
                                 n_encuestador== "josefina_ahuile_munoz" ~ "Valeria Carvajal",
                                 n_encuestador== "farid_halaby" ~ "Valeria Carvajal",
                                 n_encuestador== "venecia" ~ "Venecia Moreno",
                                 n_encuestador== "venecia_moreno" ~ "Venecia Moreno",
                                 n_encuestador== "veronica_moya" ~ "Veronica Moya",
                                 n_encuestador== "veronica_moya_" ~ "Veronica Moya",
                                 n_encuestador== "veronica_paz_moya_rosas" ~ "Veronica Moya",
                                 n_encuestador== "victor" ~ "Victor Avalos",
                                 n_encuestador== "victor_avalos" ~ "Victor Avalos",
                                 n_encuestador== "ignacia_fica" ~ "Ricardo Quiroz",
                                 n_encuestador== "vicente" ~ "Consuelo Llanten",
                                 n_encuestador== "noel_casas_-cordero_y_samanta_letelier_" ~ "Amanda Baez",
                                 n_encuestador== "benjamin_(iris)" ~ "Venecia Moreno",
                                 TRUE ~ n_encuestador))
table(base_antropologia$n_encuestador)

# ea_05_que_tan_satisfecho_esta_con_tu_rendimiento_academico_en_el_ultimo_semestre_finalizado_considere_el_ultimo_semestre_finalizado_como_el_segundo_semestre_del_ano_2023",
unique(base_antropologia$ea_05) # recodificar en 2: SAMANTA

base_antropologia <- base_antropologia %>% dplyr::rename(satisfaccion_rendimiento_academico = ea_05)
names(base_antropologia)
unique(base_antropologia$satisfaccion_rendimiento_academico)
table(base_antropologia$satisfaccion_rendimiento_academico)
class(base_antropologia$satisfaccion_rendimiento_academico)
base_antropologia <- base_antropologia %>% 
  mutate(satisfaccion_rendimiento_academico = as.factor(satisfaccion_rendimiento_academico))

base_antropologia <- base_antropologia %>% 
  mutate(satisfaccion_rendimiento_academico = case_when(satisfaccion_rendimiento_academico== "Insatisfecho" ~ "Insatisfecho",
                                                        satisfaccion_rendimiento_academico== "Muy insatisfecho" ~ "Insatisfecho",
                                                        satisfaccion_rendimiento_academico== "Muy Satisfecho" ~ "Satisfecho",
                                                        satisfaccion_rendimiento_academico== "Satisfecho" ~ "Satisfecho"))

table(base_antropologia$satisfaccion_rendimiento_academico)

# ea_03_como_describiria_su_carga_academica_actual"
unique(base_antropologia$ea_03) # transformar en factor y ordenar: SAMANTA

base_antropologia <- base_antropologia %>% dplyr::rename(descripcion_carga_academica = ea_03)
names(base_antropologia)
class(base_antropologia$descripcion_carga_academica)

base_antropologia <- base_antropologia %>% 
  mutate(descripcion_carga_academica = as.factor(descripcion_carga_academica))
unique(base_antropologia$descripcion_carga_academica)



# renombro las sociodemográficas: 
names(base_antropologia)
base_antropologia <- base_antropologia %>% dplyr::rename()
unique(base_antropologia$sd_03)



unique(base_antropologia$sd_01) # 
unique(base_antropologia$sd_02) # NOEL 

table(base_antropologia$edad) # NOEL
unique(base_antropologia$edad)

#Rename sd_03
#primero la cambio el nombre a la variable
base_antropologia <- base_antropologia %>% dplyr::rename (edad =sd_03)
names(base_antropologia)
unique(base_antropologia$edad)

base <- base %>% mutate(variable_elegida=case_when(variable_elegida=="valor respuesta dada"~"Nuevo valor de la categoría",
                                                   variable_elegida=="valor respuesta dada"~"Nuevo valor de la categoría",
                                                   variable_elegida=="valor respuesta dada"~"Nuevo valor de la categoría",
                                                   TRUE ~ ocupacion_madre))


base_antropologia <- base_antropologia %>% mutate(edad=case_when(edad=="23.0"~"23",
                                            edad=="20.0"~"20",  
                                            edad=="22.0"~"22",
                                            edad=="24.0"~"24",
                                            edad=="21.0"~"21",
                                            edad=="21 años"~"21", 
                                            edad=="23 años"~"23",
                                            edad=="18.0"~"18",
                                            edad=="41.0"~"41",
                                            edad=="28.0"~"28",
                                            edad=="19.0"~"19",
                                            edad=="27.0"~"27",
                                            edad=="20 años"~"20",
                                            edad=="30.0"~"30",
                                            edad=="25.0"~"25",
                                            edad=="26.0"~"26",
                                            edad=="22 años"~"22", 
                                            edad=="20 años "~"20",
                                            edad=="19 años "~"19",
                                            edad=="18 años"~"18",
                                            edad=="31.0"~"31",
                                            edad=="40.0"~"40",
                                            TRUE ~ edad))
unique(base_antropologia$edad)

#ahora construyo una nueva variable con rangos


base_antropologia$edad <- as.numeric(base_antropologia$edad)
class(base_antropologia$edad)

base_antropologia <- base_antropologia %>% 
  mutate (edad_r= case_when (edad %in% c(18:20) ~ "18 a 20", 
                            edad %in% c(21:23) ~ "21 a 23", 
                            edad %in% c(24:29) ~ "24 a 29", 
                            edad >= 30 ~ "30 o más"))

str(base_antropologia)


unique(base_antropologia$sd_04) # JOAQUÍN 
unique(base_antropologia$sd_05) # MATÍAS 
unique(base_antropologia$sd_07) # JOAQUÍN
unique(base_antropologia$sd_08) # JOAQUÍN
unique(base_antropologia$sd_09)

names(base_antropologia)

# distancia a la universidad
# indice de prioridad social
# zona de la ciudad 

# Estrés académico
unique(base_antropologia$ea_01)
unique(base_antropologia$ea_02)


# ea_01_cuantas_horas_dedica_aproximadamente_al_estudio_y_a_la_realizacion_de_trabajos_universitarios_fuera_del_aula_por_cada_dia_una_semana_habil_esto_es_de_lunes_a_viernes_por_ejemplo_si_lunes_y_martes_suelo_estudiar_mas_o_menos_3_horas_miercoles_5_horas_y_finalmente_jueves_y_viernes_suelo_estudiar_2_horas_el_total_de_horas_es_15_dividido_por_15_por_5_me_da_3_deberia_marcar_la_alternativa_b_3_o_4_horas",
class(base_antropologia$ea_01) # transformar en factor y ordenar: NOEL 

#primero la cambio el nombre a la variable
base_antropologia <- base_antropologia %>% dplyr::rename (horas_estudio_semana = "ea_01"  )
names(base_antropologia)
unique(base_antropologia$horas_estudio_semana)
table(base_antropologia$horas_estudio_semana)

#cambio a factor
class(base_antropologia$horas_estudio_semana)

base_antropologia <- base_antropologia %>%
  mutate(horas_estudio_semana = as.factor(horas_estudio_semana))


# ea_02_cuantas_horas_dedica_aproximadamente_al_estudio_cada_dia_a_lo_largo_del_fin_de_semana_sabado_y_domingo",
unique(base_antropologia$ea_02) # transformar en factor y ordenar: NOEL 

#primero la cambio el nombre a la variable
base_antropologia <- base_antropologia %>% dplyr::rename (horas_estudio_fin_semana = "ea_02"  )
names(base_antropologia)

#cambio a factor
class(base_antropologia$horas_estudio_fin_semana)

base_antropologia <- base_antropologia %>%
  mutate(horas_estudio_fin_semana = as.factor(horas_estudio_fin_semana))

# ea_03_como_describiria_su_carga_academica_actual"
unique(base_antropologia$ea_03) # transformar en factor y ordenar: SAMANTA

# ea_04_en_el_ultimo_semestre_finalizado_aproximadamente_que_promedio_de_notas_ha_obtenido_considere_el_ultimo_semestre_finalizado_como_el_segundo_semestre_del_ano_2023",
unique(base_antropologia$ea_04) # recodificar a número, recodificar a rangos: MATIAS

# ea_05_que_tan_satisfecho_esta_con_tu_rendimiento_academico_en_el_ultimo_semestre_finalizado_considere_el_ultimo_semestre_finalizado_como_el_segundo_semestre_del_ano_2023",
unique(base_antropologia$ea_05) # recodificar en 2: SAMANTA

# ea_06_en_una_escala_del_1_al_5_donde_1_es_minimo_estres_y_5_es_maximo_estres_como_calificaria_su_nivel_de_estres_en_la_universidad_en_el_ultimo_semestre_finalizado",
unique(base_antropologia$ea_06) # recodificar en 2: Joaquín

# ea_07_en_que_medidas_el_estres_afecta_su_rendimiento_academico",
unique(base_antropologia$ea_07) # recodificar en 2: Joaquín

# ea_08_puede_identificar_por_si_mismo_cuando_se_siente_estresado_debidos_a_factores_relacionados_con_el_ambito_universitario",
unique(base_antropologia$ea_08)

# ea_09_cuando_esta_en_periodos_de_evaluaciones_academicas_ha_tenido_alguno_de_estos_sintomas_seleccione_todas_las_alternativas_que_correspondan_con_su_caso",
unique(base_antropologia$ea_09) # SEBASTIÁN
class(base_antropologia$ea_09)

# RESPUESTA MÚLTIPLE 
# ea_09_cuando_esta_en_periodos_de_evaluaciones_academicas_ha_tenido_alguno_de_estos_sintomas_seleccione_todas_las_alternativas_que_correspondan_con_su_caso",
unique(base_antropologia$ea_09) # SEBASTIÁN
class(base_antropologia$ea_09)


#separo las respuestas y creo un vector que las lista
respuestas <- strsplit(base_antropologia$ea_09, ",") # separo las respuestas que tienen coma (,)
respuestas <- unlist(respuestas) #las unlisto, las saco de una lista
unique(respuestas)


#observo las respuestas
freq(respuestas, prop=TRUE, order = "freq", report.nas = FALSE) %>% 
  tb()

#elimino espacio antes de primera letra
respuestas_limpio <- trimws(respuestas, which = "left")

# obtengo las frecuencias de mis preguntas de respuesta múltiple
freq(respuestas_limpio, prop=TRUE, order = "freq", report.nas = FALSE) %>% 
  tb()

#Guardo para graficar
ea_09_graf <- freq(respuestas_limpio, prop=TRUE, order = "freq", report.nas = FALSE) %>% 
  tb()

ea_09_tabla <- freq(respuestas_limpio, prop=TRUE, order = "freq", report.nas = FALSE) %>% 
  tb() %>%
  kable(col.names = c("Síntoma", "Frecuencia", "%", "% Acumulado"),
        caption = "Síntomas de Estress", 
        format = "html", digits = 2) %>%  #le doy formate con kable
  kable_classic(full_width = F, html_font = "Cambria") %>% 
  save_kable(file = "outputs/ea_09_tabla.png", zoom = 3)



# renombro nombre de mi tabla
ea_09_graf <-  ea_09_graf %>% 
  rename(Problema = value, Porcentaje= pct)

# realizo gráfico
g_ea_09_graf <- ggplot(ea_09_graf, aes(x = Porcentaje, y = fct_reorder(Problema, Porcentaje), fill= Problema)) +
  geom_col() +
  labs(title = "Síntomas de Estrés Académico",
       subtitle = "según datos de Encuestas Estudiantes Antropología 2024",
       x = "%",
       y = "Síntoma") +
  geom_text(data = ea_09_graf %>% filter(rank(-Porcentaje) <= 12), # Solo añadir texto a las primeras 8 categorías
            aes(label = ifelse(rank(-Porcentaje) <= 12, paste0(round(Porcentaje, 1), "%"), "")),
            hjust = 1, size = 3, nudge_x = -.9, fontface= "bold", color = "white") +
  scale_fill_viridis_d(option = "C", guide = "none") +
  theme_ipsum()



ggsave("outputs/g_ea_09_graf.png", plot = g_ea_09_graf, width = 10, height = 7, dpi = 300)

# ea_10_que_estrategias_utiliza_con_mayor_frecuencia_para_manejar_el_estres_academico_seleccione_todas_las_alternativas_que_correspondan_con_su_caso",
unique(base_antropologia$ea_10) # NOEL 




# Exportar ----------------------------------------------------------------

write.xlsx(x = base_antropologia,file = "base_antropologia_limpia")
