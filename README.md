    def gold_room
      puts "This room is full of gold. How much do you take?"
    print "> "
    
    choice = $stdin.gets.chomp
    #this line has a bug, so fix it
      if choice =~/0/ || choice =~/1/
        how_much = choice.to_i
      else
        dead("Man, learn to type a number.")
    end
    
      if how_much < 50
      puts "Nice, you're not greedy, you win!"
	  exit(0)
    else 
      dead("You greedy bastard!")
    end
    end
 
    def moustach_room
    puts "В комнате усатое чудовище."
    puts "У чудовища много власти."
    puts "Чудовище заставляет вас меньше курить."
    puts "Что вы хотите сделать с чудовищем?"
    bear_moved = false
	
    while true
	  print "> "
	  choice = $stdin.gets.chomp
	  
	    if choice == "take honey"
	      dead("The bear looks at you then slaps your face off.")
	    elsif choice == "taunt bear" && !bear_moved
	      puts "The bear has moved from the door. You can go through it now."
	      bear_moved = true
	    elsif choice == "taunt bear" && bear_moved
	      dead("The bear get pissed off and chews your leg off.")
	    elsif choice == "open door" && bear_moved
	      gold_room
	    else 
	      puts "Пиши пиши, только по английски пиши"
	    end
    end
    end
	
    def cthulhu_room
    puts "Here you see the great evil Cthulhu."
    puts "He, it, whatever stares at you and you go insane."
    puts "Do you flee for your life or eat your head?"
	  
    print "> "
    choice = $stdin.gets.chomp
	if choice.include? "flee"
	  start
	elsif (choice.include? "head")
	  dead("Well that was tasty!")
	else 
	  cthulhu_room
	end
    end
	 
    def dead(why)
    puts why, "Good job!"
    exit(0)
    end
	
    def start
    puts "Вы пришли на работу."
    puts "Вам хочется поскорее зарплату. Вам нужно поискать Аллу по кабинетам"
    puts "В какой кабинет вы хотите пойти?(201, 402, 408)"
	  
    print"> "
    choice = $stdin.gets.chomp
	  
	if choice == "201"
	  moustach_room
	elsif choice == "402"
	  leprekon_room
	elsif choice == "408"
	  hr_room
	else 
	  dead("Вы слишком долго бродили по кабинетам. Вас заметили и уволили")
	end
    end
	 
    start
