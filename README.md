# ruby-learning-path

This is a document containing the most important things about ruby, and tends to be a learning path to Ruby as to become a proficient developer in this language.

The guide will be divided in three components aimed to be followed in order:

1. A gentle introduction to the Ruby sintax and singularities.
   
        - To get a quick overview on the Ruby language and sintax, [Ruby in 20 minutes](https://www.ruby-lang.org/en/documentation/quickstart/) needs to be your first option.
  
        - For differences between Ruby and other languages, [Ruby unique traits & Ruby for other languages](https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/) may be handy, and also presents comparisons between Ruby and [C and C++](https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-c-and-cpp/), [Java](https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-java/), [Perl](https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-perl/), [PHP](https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-php/) and [Python](https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/). 
  
        - To be more alligned on Ruby best practices, you can refer to : [Ruby style guide](https://github.com/rubocop-hq/ruby-style-guide)
  
2. A theorical and practical primer on the main concepts of Ruby.
        - Learn Ruby The Hard Way
        *Disclaimer: there are lessons that I didn't find so useful, but if you feel the need to check them out, you can find them in [The 'Learn Ruby The Hard Way' website](https://learnrubythehardway.org/book)*
        
            - [String Formatting](https://learnrubythehardway.org/book/ex8.html)
            - [Prompting to the user](https://learnrubythehardway.org/book/ex11.html)
            - [Program Arguments](https://learnrubythehardway.org/book/ex13.html)
            - [Reading files](https://learnrubythehardway.org/book/ex15.html)
            - [File manipulation](https://learnrubythehardway.org/book/ex16.html)
            - [Working with modules](https://learnrubythehardway.org/book/ex25.html)
            - [Conditionals](https://learnrubythehardway.org/book/ex30.html)
            - [Arrays and Loops](https://learnrubythehardway.org/book/ex32.html)
            - [Symbols (Idiomatic cheatsheet)](https://learnrubythehardway.org/book/ex37.html)
            - [Hashmaps](https://learnrubythehardway.org/book/ex39.html)
            - [Modules, Classes and Objects](https://learnrubythehardway.org/book/ex40.html)
            - [Object-Oriented Ruby](https://learnrubythehardway.org/book/ex41.html)
                *For more OOP exercises, you can also use [Excercise 42](https://learnrubythehardway.org/book/ex42.html), [Execise 43](https://learnrubythehardway.org/book/ex43.html) and [Exercise 44](https://learnrubythehardway.org/book/ex44.html)
            - [Project Structure](https://learnrubythehardway.org/book/ex46.html)
            - [Writing tests](https://learnrubythehardway.org/book/ex47.html)

        - Programming Ruby
        Programming Ruby is a documentation site with a lot of helpful information on Ruby. I will only add the links that add something of value which we didn't found on Ruby the Hard Way, or the ones that are not covered in that book.
            - [Expressions](https://ruby-doc.com/docs/ProgrammingRuby/html/tut_expressions.html)
            - [Handling Exceptions](https://ruby-doc.com/docs/ProgrammingRuby/html/tut_exceptions.html)
            - [Threads](https://ruby-doc.com/docs/ProgrammingRuby/html/tut_threads.html)
            - [Reflection](https://ruby-doc.com/docs/ProgrammingRuby/)
                *Reflection is the ability to look under the hood on a class or object in order to understand for example, which methods can be called.*
            - [Modules](https://ruby-doc.com/docs/ProgrammingRuby/html/tut_modules.html)
                *Including files & mixins.*
3. Useful Libraries
        - Ethereum/related libraries:
            * [Ethereum Ruby library](https://github.com/EthWorks/ethereum.rb) and this [helpful tutorial](https://medium.com/@rubyruby.ru/dive-into-ethereum-development-part-3-user-application-107f0a6e5190)
            * [Web3 RPC client for Ethereum node](https://rubygems.org/gems/web3-eth/versions/0.1.0)
            * [~Another~ Web3 RPC client for Ethereum node](https://github.com/izetex/web3-eth)
            * [A simple Ethereum library for Ruby](https://github.com/DigixGlobal/ethereum-ruby)
            
4. Notes on the different issues I have come across.
    
        - Installing a gem
            [RubyGems](https://rubygems.org/) is the package manager of Ruby, which can be helpful for you in the development process. For example, in my case I wanted to install [SQLITE3](https://rubygems.org/gems/sqlite3/versions/1.3.11) to be able to easily interact with a SQLite database.
            To install a gem, the command used is:
            `gem install <gemName>`
            But, running that command was ending with an error:
            ```
            ERROR: Failed to build gem native extension.
                current directory: /var/lib/gems/2.5.0/gems/nokogiri-1.10.3/ext/nokogiri
                /usr/bin/ruby2.5 -r ./siteconf20190807-22036-snjnej.rb extconf.rb mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h
                extconf failed, exit code 1

                Gem files will remain installed in /var/lib/gems/2.5.0/gems/n-okogiri-1.10.3 for inspection.
                Results logged to /var/lib/gems/2.5.0/extensions/x86_64-linux/2.5.0/nokogiri-1.10.3/gem_make.out
            ```
            
            Which seems to be a problem on the header files, but after Googling for a bit, I found the command needed to install the ruby-dev dependencies that are needed to fix this problem in an Ubuntu box:
            `sudo apt-get install ruby`ruby -e 'puts RUBY_VERSION[/\d+\.\d+/]'`-dev`
            
            Also, at this point I added the Ruby package path to source by running:
            
            `gem env` and grabbing the "RUBY E XECUTABLE" value, and then:
            
            `export PATH=$PATH:/var/lib/gems/2.5.0/`
            

            Nevertheless, once I ran again the command, I encountered another error:
            ```
            Fetching: sqlite3-1.4.1.gem (100%)
                Building native extensions. This could take a while...
                ERROR:  Error installing sqlite3:
                        ERROR: Failed to build gem native extension.

                    current directory: /var/lib/gems/2.5.0/gems/sqlite3-1.4.1/ext/sqlite3
                /usr/bin/ruby2.5 -r ./siteconf20190807-9493-wzuepa.rb extconf.rb
                checking for sqlite3.h... no
                sqlite3.h is missing. Try 'brew install sqlite3',
                'yum install sqlite-devel' or 'apt-get install libsqlite3-dev'
                and check your shared library search path (the
                location where your sqlite3 shared library is located).
                *** extconf.rb failed ***
                Could not create Makefile due to some reason, probably lack of necessary
                libraries and/or headers.  Check the mkmf.log file for more details.  You may
                need configuration options.

                Provided configuration options:
                        --with-opt-dir
                        --without-opt-dir
                        --with-opt-include
                        --without-opt-include=${opt-dir}/include
                        --with-opt-lib
                        --without-opt-lib=${opt-dir}/lib
                        --with-make-prog
                        --without-make-prog
                        --srcdir=.
                        --curdir
                        --ruby=/usr/bin/$(RUBY_BASE_NAME)2.5
                        --with-sqlcipher
                        --without-sqlcipher
                        --with-sqlite3-config
                        --without-sqlite3-config
                        --with-pkg-config
                        --without-pkg-config
                        --with-sqlcipher
                        --without-sqlcipher
                        --with-sqlite3-dir
                        --without-sqlite3-dir
                        --with-sqlite3-include
                        --without-sqlite3-include=${sqlite3-dir}/include
                        --with-sqlite3-lib
                        --without-sqlite3-lib=${sqlite3-dir}/lib

                To see why this extension failed to compile, please check the mkmf.log which can be found here:

                /var/lib/gems/2.5.0/extensions/x86_64-linux/2.5.0/sqlite3-1.4.1/mkmf.log

                extconf failed, exit code 1

                Gem files will remain installed in /var/lib/gems/2.5.0/gems/sqlite3-1.4.1 for inspection.
                Results logged to /var/lib/gems/2.5.0/extensions/x86_64-linux/2.5.0/sqlite3-1.4.1/gem_make.out
            ```
            
            This error was because of missing dependencies (again), and the command to add them is:
            `sudo apt-get install libsqlite3-dev`
            
            Now, you can run `gem install sqlite3` and everything will work correctly
            So, you can take two takeaways from this errors:
                - Add your Gem folder to PATH.
                - You may be missing some dependencies to install the correct Gem, so search for the error in [DuckDuckGo](https://duckduckgo.com/) and enjoy the slick StackoverFlow widget they have on their search engine.
