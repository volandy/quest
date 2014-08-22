    def gold_room
      puts "This room is full of gold. How much do you take?"
    print "> "
    choice = $stdin.gets.chomp
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
    puts "Чудовище заставляет вас сделать норму."
    puts "Что вы хотите сделать с чудовищем?"
    puts "Дать по усам(1)"
    puts "Попросить повышение(2)"
    puts "Отработать норму(3)"
    pen_gained = false
	
    while true
	  print "> "
	  choice = $stdin.gets.chomp
	  
	    if choice == "1"
	      dead("Вас уволили за неуважительное отношение к менеджменту.")
	    elsif choice == "2"  
	      puts "Вам дали подписать ворнинг"
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
	
    def leprekon_room
    puts "Вы видите лепрекона сидящего на горшке с золотом."
    puts "Он не тратит золото а только копит его."
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
    
    def nose_room
    end
	 
    def dead(why)
    puts why, "Конец!"
    exit(0)
    end
	
    def start
    puts "Вы пришли на работу."
    puts "Вам хочется поскорее зарплату. Вам нужно найти Аллу чтобы подписать аннекс"
    puts "В какой кабинет вы хотите пойти?(201, 402, 408)"
	  
    print"> "
    choice = $stdin.gets.chomp
	  
	if choice == "201"
	  moustach_room
	elsif choice == "402"
	  leprekon_room
	elsif choice == "408"
	  nose_room
	else 
	  dead("Вы превысили время перерыва. Вас заметили и уволили")
	end
    end
	 
    start
