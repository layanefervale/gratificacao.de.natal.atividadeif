# gratificacao.de.natal.atividadeif
Atividade de IF feita no github 
public class Employee {
	
	private int hourPrize;
	private String minuteExtra;
	private String minuteLacked;
	

	//Construtor para inicializar com parâmetros
	public Employee( String extra, String lacked ){
		this.setMinuteExtra( extra );
		this.setMinuteLacked( lacked );
	}
	
	public void setMinuteExtra( String extra ){
		this.minuteExtra = extra;
	}
	
	public int getMinuteExtra(){
		return Integer.parseInt( this.minuteExtra );
	}
	
	public void setMinuteLacked( String lacked ){
		this.minuteLacked = lacked;
	}
	
	public int getMinuteLacked(){
		return Integer.parseInt( this.minuteLacked );
	}
	
	//função para converter a hora extra, em um horário de
	//com base nos minutos dados
	public String getHourExtra(){
		int hour = 0, minute = 0, second = 0;
		String resulted;
		
		if( this.getMinuteExtra() > 59 ){
			hour = this.getMinuteExtra() / 60;
			minute = this.getMinuteExtra() % 60;
			second = 0;
		}else{
			if( this.getMinuteExtra() <= 59 ){
				hour = 0;
				minute = this.getMinuteExtra();
				second = 0;
			}
		}
		
		resulted = String.valueOf( ""+ hour +":"+ minute +":"+ second );
		
		return resulted;
	}
	
	//função para converter a hora faltada, em um horário de
	//com base nos minutos dados
	public String getHourLacked(){
		int hour = 0, minute = 0, second = 0;
		String resulted;
		
		if( this.getMinuteLacked() > 59 ){
			hour = this.getMinuteLacked() / 60;
			minute = this.getMinuteLacked() % 60;
			second = 0;
		}else{
			if( this.getMinuteLacked() <= 59 ){
				hour = 0;
				minute = this.getMinuteLacked();
				second = 0;
			}
		}
		
		resulted = String.valueOf( ""+ hour +":"+ minute +":"+ second );
		
		return resulted;
	}
	
	//função que retorna o valor do prêmio
	public double valuePrize(){
		double result = 0.0;
		
		this.hourPrize = this.getMinuteExtra() - this.getMinuteLacked();
		
		 if( this.hourPrize >= 2400 ) 
		 	result = 500.00;
         else  
           	if( this.hourPrize >= 1800 && this.hourPrize < 2400 ) 
           		result = 400.00;
           	else  
               	if( this.hourPrize >= 1200 && hourPrize < 1800 ) 
               		result = 300.00;
               	else  
                   	if( this.hourPrize >= 600 && this.hourPrize < 1200 )  
                   		result = 200.00;
                  	else
                  		result = 100.00;
                  		
         return result;
    }
	
	public String toString(){
		return String.format( "%s: %s\n%s: %s\n%s: %.2f", 
			"Hour Extra", this.getHourExtra(),
			"Hour Lacked", this.getHourLacked(),
			"Value of Prize", this.valuePrize() );
	}
}
class principal:


 import javax.swing.JOptionPane;
 
public class HoursEmployee {
    
    public static void main(String[] args) {
     	
     	String hourExtra = "";
     	String hourLacked = "";
     	
     	hourExtra = JOptionPane.showInputDialog( "Type the hour extra: " );
     	hourLacked = JOptionPane.showInputDialog( "Type the hour lacked: " );
             
     	Employee employee = new Employee( hourExtra, hourLacked );
     	
     	//imprime resultado por função maneira normal
     	System.out.printf( "%s: %s\n%s: %s\n%s: %.2f", 
			"Hour Extra", employee.getHourExtra(),
			"Hour Lacked", employee.getHourLacked(),
			"Value of Prize", employee.valuePrize() );
     	
     	//imprime resultado pelo objeto da class
     	System.out.printf( "\n\n%s", employee );
    }
}


