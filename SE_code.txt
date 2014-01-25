import java.sql.SQLException;


public class TestGUI {

	public static void main(String[] args) {
		Object admin;
		Object user1;
		Object ah;
		
		
		SelectUser user=new SelectUser();
		user.setVisible(true);
		
		
		try {
			Dbconnect.DbCall();
		} catch (InstantiationException | IllegalAccessException
				| ClassNotFoundException | SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		

	}

}



import java.sql.*;


public class Dbconnect  {

	
	
		
	public static void DbCall() throws SQLException, InstantiationException, IllegalAccessException, ClassNotFoundException {
		
		int i=0;
		String[] pinCat = new String[50];
		
		
		
		//Database connection
	
			
		Class.forName("com.mysql.jdbc.Driver").newInstance();
		String connectionUrl = "jdbc:mysql://localhost:3306/auction";
		String connectionUser = "root";
		String connectionPassword = "root";
		Connection conn = DriverManager.getConnection(connectionUrl, connectionUser,
		connectionPassword);
			
		
		
		
		Statement stmt = conn.createStatement();
		
		
		ResultSet rs = stmt.executeQuery("SELECT * FROM category");
		while (rs.next())
		{
			
			
		String category = rs.getString("category");
		
		pinCat[i]=category;
		i++;
		
		
		}
		
		
		for(int j = 0; j < i; j++)
		
			System.out.println("Category: " + pinCat[j]);
		
	
     }
	
		
	

}


import java.awt.BorderLayout;


public class SelectUser extends JFrame {

	private JPanel contentPane;
	JTextField textField;

	/**
	 * Launch the application.
	 */
	
	
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					SelectUser frame = new SelectUser();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public SelectUser() {
		setTitle("Select User");
		setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
		setBounds(100, 100, 496, 384);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		final JRadioButton rdbtnNewRadioButton = new JRadioButton("");
		rdbtnNewRadioButton.setBounds(145, 114, 51, 23);
		contentPane.add(rdbtnNewRadioButton);
		
		final JRadioButton rdbtnNewRadioButton_1 = new JRadioButton("");
		rdbtnNewRadioButton_1.setBounds(145, 173, 51, 23);
		contentPane.add(rdbtnNewRadioButton_1);
		
		JLabel lblNewLabel = new JLabel("\u0394\u03B9\u03B1\u03C7\u03B5\u03B9\u03C1\u03B9\u03C3\u03C4\u03AE\u03C2");
		lblNewLabel.setBounds(26, 114, 95, 14);
		contentPane.add(lblNewLabel);
		
		JLabel lblNewLabel_1 = new JLabel("\u0391\u03C0\u03BB\u03CC\u03C2 \u03A7\u03C1\u03AE\u03C3\u03C4\u03B7\u03C2");
		lblNewLabel_1.setBounds(26, 173, 113, 14);
		contentPane.add(lblNewLabel_1);
		
		JButton btnNewButton = new JButton("\u0388\u03BE\u03BF\u03B4\u03BF\u03C2");
		btnNewButton.addActionListener(new ActionListener() {
			
			public void actionPerformed(ActionEvent e) {
				System.exit(0);
				
			}
		});
		btnNewButton.setBounds(329, 255, 109, 23);
		contentPane.add(btnNewButton);
		
		JButton btnNewButton_1 = new JButton("\u0395\u03AF\u03C3\u03BF\u03B4\u03BF\u03C2");
		btnNewButton_1.addActionListener(new ActionListener() {
			
			public void actionPerformed(ActionEvent arg0) {
				
				String pass = textField.getText();
				
				if (pass.equals("admin") && rdbtnNewRadioButton.isSelected()){
					
					Administrator admin=new Administrator();
					admin.setVisible(true);
					
					
				}else if (rdbtnNewRadioButton_1.isSelected()){
					
					User user1=new User();
				   user1.setVisible(true);
				
				
				}
				
				
			}
		});
		btnNewButton_1.setBounds(329, 221, 109, 23);
		contentPane.add(btnNewButton_1);
		
		textField = new JTextField();
		textField.setBounds(329, 117, 86, 20);
		contentPane.add(textField);
		textField.setColumns(10);
		
		JLabel label = new JLabel("\u039A\u03C9\u03B4\u03B9\u03BA\u03CC\u03C2");
		label.setBounds(232, 119, 89, 14);
		contentPane.add(label);
	}
}


import java.awt.BorderLayout;


public class Administrator extends JFrame {

	private JPanel contentPane;
	private JTextField textField;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					Administrator frame = new Administrator();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	
	SelectUser user=new SelectUser();
	
	
	
	
	
	public Administrator() {
		setTitle("Administrator");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 496, 384);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		JLabel lblNewLabel = new JLabel("\u0395\u03C0\u03B5\u03BE\u03B5\u03C1\u03B3\u03B1\u03C3\u03AF\u03B1");
		lblNewLabel.setBounds(41, 106, 103, 14);
		contentPane.add(lblNewLabel);
		
		JLabel lblNewLabel_1 = new JLabel("\u039A\u03B1\u03C4\u03AC\u03C1\u03B3\u03B7\u03C3\u03B7");
		lblNewLabel_1.setBounds(41, 159, 89, 14);
		contentPane.add(lblNewLabel_1);
		
		JLabel label = new JLabel("");
		label.setBounds(41, 224, 46, 14);
		contentPane.add(label);
		
		JButton btnNewButton = new JButton("\u039A\u03B1\u03C4\u03B1\u03C7\u03CE\u03C1\u03B7\u03C3\u03B7");
		btnNewButton.setBounds(41, 274, 115, 23);
		contentPane.add(btnNewButton);
		
		JButton btnNewButton_1 = new JButton("\u0395\u03C0\u03B9\u03C3\u03C4\u03C1\u03BF\u03C6\u03AE");
		btnNewButton_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				
				
				user.setVisible(true);
				
			}
		});
		btnNewButton_1.setBounds(182, 274, 115, 23);
		contentPane.add(btnNewButton_1);
		
		JButton btnNewButton_2 = new JButton("\u0388\u03BE\u03BF\u03B4\u03BF\u03C2");
		btnNewButton_2.addActionListener(new ActionListener() {
			
			public void actionPerformed(ActionEvent e) {
				System.exit(0);
			}
		});
		btnNewButton_2.setBounds(329, 274, 115, 23);
		contentPane.add(btnNewButton_2);
		
	    JComboBox comboBox = new JComboBox();
		comboBox.setBounds(169, 130, 89, 20);
		contentPane.add(comboBox);
		

		
		textField = new JTextField();
		textField.setBounds(169, 62, 86, 20);
		contentPane.add(textField);
		textField.setColumns(10);
		
		JLabel label_1 = new JLabel("\u039A\u03B1\u03C4\u03B7\u03B3\u03BF\u03C1\u03AF\u03B1");
		label_1.setBounds(41, 65, 89, 14);
		contentPane.add(label_1);
	}
}



import java.awt.BorderLayout;


public class User extends JFrame {

	private JPanel contentPane;
	private JTextField textField;

	/**
	 * Launch the application.
	 */
	
	
	SelectUser user=new SelectUser();
	
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					User frame = new User();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public User() {
		setTitle("User");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 496, 384);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		JLabel lblNewLabel = new JLabel("\u038C\u03BD\u03BF\u03BC\u03B1");
		lblNewLabel.setBounds(46, 88, 65, 14);
		contentPane.add(lblNewLabel);
		
		JLabel lblNewLabel_1 = new JLabel("\u0395\u03C0\u03B5\u03BE\u03B5\u03C1\u03B3\u03B1\u03C3\u03AF\u03B1");
		lblNewLabel_1.setBounds(46, 148, 89, 14);
		contentPane.add(lblNewLabel_1);
		
		JLabel lblNewLabel_2 = new JLabel("\u039A\u03B1\u03C4\u03AC\u03C1\u03B3\u03B7\u03C3\u03B7");
		lblNewLabel_2.setBounds(46, 210, 89, 14);
		contentPane.add(lblNewLabel_2);
		
		JButton btnNewButton = new JButton("\u039A\u03B1\u03C4\u03B1\u03C7\u03CE\u03C1\u03B7\u03C3\u03B7");
		btnNewButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				
				String name = textField.getText();
				if (!name.equals("")){
					
					AuctionHouse house=new AuctionHouse();
					house.setVisible(true);
					
					
				}
				
			}
		});
		btnNewButton.setBounds(46, 274, 115, 23);
		contentPane.add(btnNewButton);
		
		JButton btnNewButton_1 = new JButton("\u0395\u03C0\u03B9\u03C3\u03C4\u03C1\u03BF\u03C6\u03AE");
		btnNewButton_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				
				user.setVisible(true);
			}
		});
		btnNewButton_1.setBounds(189, 274, 115, 23);
		contentPane.add(btnNewButton_1);
		
		JButton btnNewButton_2 = new JButton("\u0388\u03BE\u03BF\u03B4\u03BF\u03C2");
		btnNewButton_2.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				
				System.exit(0);
			}
		});
		btnNewButton_2.setBounds(337, 274, 115, 23);
		contentPane.add(btnNewButton_2);
		
		textField = new JTextField();
		textField.setBounds(152, 85, 115, 20);
		contentPane.add(textField);
		textField.setColumns(10);
		
		JComboBox comboBox = new JComboBox();
		comboBox.setBounds(152, 177, 115, 20);
		contentPane.add(comboBox);
		
		JLabel label = new JLabel("\u0394\u03B7\u03BC\u03BF\u03C0\u03C1\u03B1\u03C3\u03AF\u03B1");
		label.setBounds(155, 60, 112, 14);
		contentPane.add(label);
		
		JLabel lblNewLabel_3 = new JLabel("\u03A5\u03C0\u03AC\u03C1\u03C7\u03BF\u03C5\u03C3\u03B1 \u0394\u03B7\u03BC\u03BF\u03C0\u03C1\u03B1\u03C3\u03AF\u03B1");
		lblNewLabel_3.setBounds(152, 148, 142, 14);
		contentPane.add(lblNewLabel_3);
	}

}



import java.awt.BorderLayout;


public class AuctionHouse extends JFrame {

	private JPanel contentPane;
	private JTextField textField;
	private JTextField textField_1;
	private JTextField textField_2;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					AuctionHouse frame = new AuctionHouse();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 * 
	 */
	
	
	
	public AuctionHouse() {
		setTitle("Auction House");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 496, 384);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		JLabel label = new JLabel("\u038C\u03BD\u03BF\u03BC\u03B1");
		label.setBounds(24, 46, 64, 14);
		contentPane.add(label);
		
		textField = new JTextField();
		textField.setBounds(138, 43, 86, 20);
		contentPane.add(textField);
		textField.setColumns(10);
		
		JLabel label_1 = new JLabel("\u0394\u03B9\u03AC\u03C1\u03BA\u03B5\u03B9\u03B1");
		label_1.setBounds(24, 100, 78, 14);
		contentPane.add(label_1);
		
		textField_1 = new JTextField();
		textField_1.setBounds(138, 97, 86, 20);
		contentPane.add(textField_1);
		textField_1.setColumns(10);
		
		JLabel lblNewLabel = new JLabel("\u03A4\u03B9\u03BC\u03AE");
		lblNewLabel.setBounds(24, 145, 64, 14);
		contentPane.add(lblNewLabel);
		
		textField_2 = new JTextField();
		textField_2.setBounds(138, 142, 86, 20);
		contentPane.add(textField_2);
		textField_2.setColumns(10);
		
		JLabel label_2 = new JLabel("\u039A\u03B1\u03C4\u03B7\u03B3\u03BF\u03C1\u03AF\u03B1");
		label_2.setBounds(24, 196, 78, 14);
		contentPane.add(label_2);
		
		JComboBox comboBox = new JComboBox();
		comboBox.setBounds(138, 193, 86, 20);
		contentPane.add(comboBox);
		
		JLabel label_3 = new JLabel("\u03A3\u03C7\u03CC\u03BB\u03B9\u03B1");
		label_3.setBounds(295, 46, 64, 14);
		contentPane.add(label_3);
		
		JTextArea textArea = new JTextArea();
		textArea.setBounds(292, 71, 160, 117);
		contentPane.add(textArea);
		
		JButton btnNewButton = new JButton("\u039A\u03B1\u03C4\u03B1\u03C7\u03CE\u03C1\u03B7\u03C3\u03B7");
		btnNewButton.setBounds(24, 274, 107, 23);
		contentPane.add(btnNewButton);
		
		JButton btnNewButton_1 = new JButton("\u0395\u03C0\u03B9\u03C3\u03C4\u03C1\u03BF\u03C6\u03AE");
		btnNewButton_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				User user=new User();
				user.setVisible(true);
			}
		});
		btnNewButton_1.setBounds(178, 274, 101, 23);
		contentPane.add(btnNewButton_1);
		
		JButton button = new JButton("\u0388\u03BE\u03BF\u03B4\u03BF\u03C2");
		button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				
				System.exit(0);
			}
		});
		button.setBounds(322, 274, 101, 23);
		contentPane.add(button);
	}
}
