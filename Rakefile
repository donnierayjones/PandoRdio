require "rubygems"

output_dir = './pandordio-chrome/'

desc "Nuke temp build directory and Chrome Extension lib"
task :nuke do
  puts "nuking #{output_dir}lib"
  FileUtils.rm_rf "#{output_dir}lib"

  puts "nuking ./build"
  FileUtils.rm_rf "./build"
end

desc "Compile using r.js optimization"
task :rjs => [:nuke] do
  puts "executing r.js compilation"
  %x{node ./r.js -o app.build.js}
end

desc "Copy r.js compilation and Rdio API to Chrome Extension"
task :copy => [:rjs] do
  puts "copying ./rdio-api/lib to #{output_dir}"
  FileUtils.cp_r './rdio-api/lib', "#{output_dir}"

  puts "copying ./build/build.js to #{output_dir}"
  FileUtils.cp './build/build.js', "#{output_dir}"
end

task :default => :copy
