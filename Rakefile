# install package:
#     sudo npm install beautifier
# 
#   more about beautifier:
#       https://github.com/rickeyski/node-beautifier

bin = `npm bin`.chomp

desc "compile the grammar aSb_ugly.jison"
task :default => %w{aSb_ugly.js} do
  sh "mv aSb.js aSb_ugly.js"
  sh "#{bin}/beautifier aSb_ugly.js > aSb.js"
  sh "rm -f aSb_ugly.js"
end

file "aSb_ugly.js" => %w{aSb.jison} do
  sh "jison aSb.jison aSb.l -o aSb.js"
end

desc "compile the grammar aSb_ugly.jison with -t option"
task :trace => %w{taSb_ugly.js} do
  sh "#{bin}/beautifier taSb_ugly.js > aSb.js"
  sh "rm -f taSb_ugly.js"
end

file "taSb_ugly.js" => %w{aSb.jison} do
  sh "jison aSb.jison --debug 64"
  sh "mv aSb.js taSb_ugly.js"
end

desc "Generates out.pdf containing the listings"
task :print do
  sh "a2ps --columns=1 -f 8 -R aSb.js  -o out.ps"
  #sh "a2ps --columns=1 -f 8 -R aSb_anotado.js -o out.ps"
  sh "ps2pdf out.ps out.pdf"
end

task :clean do
  sh 'rm -f out.pdf out.ps out.ps~ aSb_ugly.js'
end
