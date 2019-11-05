# jdbcSQLBasico
conexion a Mysql con conector jdbc 5.1.48

package org.datos;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class AccesoBasico {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			//Primer paso
			Class.forName("com.mysql.jdbc.Driver"); //Busca la clase Driver en las librerias
			System.out.println("Conector OK!");
			//Segundo paso
			String url = "jdbc:mysql://localhost:3306/primera";
			String user = "root";
			String password = "";
			Connection conn = DriverManager.getConnection(url, user, password);
			System.out.println("La conexion es: " + conn.toString());
			//Tercer paso
			String consulta = "select * from clientes";
			Statement st = conn.createStatement();
			ResultSet resultado = st.executeQuery(consulta);
			System.out.println("El ResultSet es: " + resultado);
			//Cuarto paso
			while(resultado.next()) {
				System.out.println(resultado.getString("nombre"));
			}
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}

}
