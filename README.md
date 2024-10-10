import UIKit
import SwipeCellKit

class ViewController: UIViewController, UITableViewDataSource, UITableViewDelegate, SwipeTableViewCellDelegate {

  @IBOutlet weak var tableView: UITableView!

  override func viewDidLoad() {
    super.viewDidLoad()
    
    // Set up table view
    tableView.dataSource = self
    tableView.delegate = self
    tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
  }

  // UITableViewDataSource methods
  func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return 10 // Number of rows in the table
  }

  func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath) as! UITableViewCell

    // Configure the cell
    cell.textLabel?.text = "Row (indexPath.row + 1)"

    // Set SwipeCellKit delegate
    let swipeCell = cell as! SwipeTableViewCell
    swipeCell.delegate = self

    // Add swipe options
    swipeCell.rightButtons=newSwipeCell.rightButtons
      // Delete button with red background
      SwipeAction(style: .destructive, title: "Delete") { action, indexPath in
        // Handle delete action
        // ...
      },
      // More button with blue background
      SwipeAction(style: .default, title: "More") { action, indexPath in
        // Handle more action
  
      }
    ]
    
    return cell
  }
  // SwipeTableViewCellDelegate method
  func tableView(_ tableView: UITableView, editActionsForRowAt indexPath: IndexPath, for orientation: SwipeActionsOrientation) -> [SwipeAction]? {
    // Create actions for each orientation
    if orientation == .right {
      return 
        // Delete button with red background
        SwipeAction(style: .destructive, title: "Delete") { action, indexPath in
          // Handle delete action
        }
        // More button with blue background
        SwipeAction(style: .default, title: "More") { action, indexPath in
          // Handle more action
        }
      ]
    } else if orientation == .left {
      return 
        // Edit button with green background
        SwipeAction(style: .default, title: "Edit") { action, indexPath in
          // Handle edit action
        }
      ]
    }
    return nil
  }

  // UITableViewDelegate method
  func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    // Handle row selection
    // ...
  }
}
