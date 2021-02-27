#!/usr/bin/env ruby

#1: Comprobar usuario root

usuario = `whoami`.chop
if usuario != "root"
  puts "||[Error] Debes usar root||"
end



#2:Argumento nulo:

if ARGV[0].nil?
  puts "||[ERROR] Se recomienda utilizar --help tras el comando||"
end



#3: Ejecutar el comando --help:


if ARGV[0] == "--help"
  puts " usage:
  	          systemctml [OPTIONS] [FILENAME]
       =========================================================================
       ========================================================================="
  puts " Options:
  	          --help, mostrar la ayuda.
                  --version, mostrar info del autor y fecha de creacion.
		  --status [FILENAME], comprueba si puede Instalar/Desistalar.
		  --run [FILENAME], Instalar/Desistalar el software indicado.
        =========================================================================
        ========================================================================="
  puts "  Description:
		  Este script se encarga de instalar/desistalar
		  el software indicado en el fichero FILENAME.

         Ejemplo de FILENAME:
		  tree:install
		  nmap:install
		  atomix:remove                                                  "
end


#4:Ejecutar el comando --version


if ARGV[0] == "--version"
  puts "
         ______________________
        |       |              |
        |AUTHOR |Gontran Fdez  |
        |-------|------------- |
        |DATE   |  22/02/2021  |
         ----------------------     "
end

#5: Ejecutar el comando --status
if ARGV[0] == "--status"
a = `cat programas.txt`.split("\n")
  a.each do |i|
b = i.split(":")
  puts "#{b[0]}"
c = `whereis #{b[0]} |grep bin |wc -l`.chop
  if c == "1"
  puts "#{b[0]}: (I) Installed"
else
  puts "#{b[0]}: (U) Unistalled"

  end
 end
 exit 0
end




#6:ARGV --run

#1: Comprobar usuario root

usuario = `whoami`.chop
if usuario != "root"
  puts "||[Error] Debes usar root||"
exit 1
end

#2: Ejecutar el comando --run

if ARGV[0] == "--run"
if ARGV[1].nil?
  puts "Parametro erroneo\n"
  puts "Utiliza `--help` para saber mas\n"
  exit 1
end

if usuario == "root"
  a = `cat #{ARGV[1]}`.split("\n")
a.each do |i|
  b = i.split(":")
  c = `whereis #{b[0]} |grep bin |wc -l`.chop

if (c == "0" && b[1] == "install")
  puts "Comenzando instalacion de #{b[0]}"
  system ("zypper install -y #{b[0]}")
  puts "\n"
end

if (c == "0" && b[1] == "remove")
  puts "Desinstalando programa #{b[0]}"
  system ("zypper remove -y #{b[0]}")
  puts "\n"
end

if (c == "1" && b[1] == "install")
  puts "#{b[0]} ya esta instalado.\n"
   end
    end
     exit 0
else
  puts "Se necesitan privilegios root.\n"
   exit 1
    end
     end
