###
User: monstersintokyo
Date: 26.01.13

Inspired by 'The little book on coffeescript'
###

fs = require 'fs'

{print} = require 'util'
{spawn} = require 'child_process'

build = (callback) ->
  coffee = spawn 'coffee', ['-c', '-o', 'js', 'coffee']
  coffee.stderr.on 'data', (data) ->
    process.stderr.write data.toString()
  coffee.stdout.on 'data', (data) ->
    print data.toString()
  coffee.on 'exit', (code) ->
    callback?() if code is 0

task 'build', 'Build js/ from src/', ->
  build()

task 'watch', 'Watch coffee/ for changes', ->
  coffee = spawn 'coffee', ['-w', '-c', '-o', 'js', 'coffee']
  coffee.stderr.on 'data', (data) ->
    process.stderr.write data.toString()
  coffee.stdout.on 'data', (data) ->
    print data.toString()

