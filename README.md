Tasker for Drupal 7
===================

Small and easy Drupal 7 module (similar to sheduler), to create and manage timed tasks for node (publishing, promoting). Based on cron.

If you want to integrate your module with Tasker, create extend for Tasker class like in example below. Don't forget to check for tasker module existing.

==========================
Example:

if(module_exists('tasker')) {
	class publish extends Tasker {
		function publish() {
			$this->title = t('Publish content');
		}
		function execute() {
			// Place here what to  do with node
			// in $this->nid you have id of current node
			// in $this->title you have title of task
			
			//here is example for publishing node with saving revision (+ log)
			$node = node_load($this->nid);
			$node->status = 1;
			$node->revision = TRUE;
			$node->log = t('Node published by Tasker');
			node_save($node);
			return TRUE;
		}
	}
}

=========================
Created by zaporylie
for Centrum Informacji i Rozwoju Spo³ecznego